SHEETFLOW
Spreadsheet Organizer
=====================

WHAT SHEETFLOW DOES
-------------------
Sheetflow is a browser-based tool for reviewing, cleaning, and exporting business
spreadsheets. Use it for inventory, customer lists, projects, orders, schedules,
service records, or any other repeated-row workflow. It helps you find repeated
records or values in a selected business field, hide rows that should not be
carried forward, and create a clean export for your team.

Your original spreadsheet is not changed. Sheetflow keeps the rows in their
original order and only excludes rows that you explicitly hide.

SUPPORTED FILES
---------------
- Excel workbooks: XLSX and XLS
- Delimited files: CSV and TSV

The application automatically looks for common fields such as:
- Record fields: product, item, customer, order, case, ticket, service, account, asset, SKU, description, or name
- Grouping fields: location, store, branch, site, warehouse, department, region, or project
- Numeric fields: quantity, amount, total, balance, score, units, or count

After import, use the Grouping field menu to choose any column that should act
as the business grouping. It can be a location, department, store, room,
project, category, or any other column in the workbook. Choose No grouping
field when grouping by that dimension is not needed. The choice is made per
worksheet and does not change the source data.

HOW TO USE SHEETFLOW
--------------------
1. Start the site and import any spreadsheet using the upload area.
2. Choose a worksheet if the workbook contains more than one sheet.
3. Choose the column to use as the Grouping field, if needed.
4. Review the data in Rows view or switch to Grouped view.
5. Search for a record, grouping field value, row number, or other cell value.
6. Hide the rows you do not want in the next export.
7. Export the cleaned result as XLSX or CSV.

GROUPING OPTIONS
----------------
The Grouping mode menu provides four ways to organize the table:

- Group by the record field
  Groups rows with the same normalized value in the detected record field.
- Group by the selected field
  Groups rows with the same normalized value in the chosen grouping field.
- Group by record + selected field
  Groups rows only when both values match.
- Group by exact row
  Groups rows when every cell value matches.

The selected-field options are available whenever a grouping field is chosen.
Any imported column can be selected, even when its header is not named
Location.

HIDING AND RESTORING ROWS
-------------------------
- Hide: hides one row while keeping it in the working data.
- Hide group: hides every row in the selected record, grouping-field, or exact-match
  group. The group is based on the current Grouping mode.
- Hide selected: hides all checked rows.
- Hide zero value: hides visible rows whose detected numeric value is zero.
- Restore selected: restores checked hidden rows.
- Restore all: restores every hidden row in the current worksheet.

To find rows that have already been hidden, turn on Include hidden beside the
search box. You can then search, select the matching rows, and use Restore
selected.

Use <empty> in the search box to find rows with a blank cell. The same token
can be used as an Automation rule value, for example Grouping field contains
<empty>, to hide rows where the selected grouping field is blank.

The Hidden rows filter is also available when you want to review all hidden
rows directly.

AUTOMATION RULES
----------------
Open Automation to create rules for recurring cleanup. A rule can match a
detected field or any imported column using Contains or Equals, then hide the
matching rows.

Example rules:
- Record contains TEST -> Hide row
- Record contains OLD -> Hide row
- Selected grouping field contains WAREHOUSE X -> Hide row
- SKU contains 12345 -> Hide row
- Selected grouping field contains <empty> -> Hide row

Rules can be enabled, disabled, edited, deleted, or run manually. They are
saved in this browser and run automatically whenever a new file is imported.
Each rule shows how many rows it affected during its last run. Automation uses
the normal hidden-row system and never deletes or changes cell values.

SEARCH, SORTING, AND VIEWS
--------------------------
Search, sorting, Rows view, Grouped view, and grouping choices only change
what is displayed. They do not delete or reorder source data.

The Hide group button uses the grouping mode currently selected. For example,
when Group by the selected field is active, Hide group hides all rows with the
same value in that field.

EXPORT RULES
------------
- Only unhidden data rows are included in exports.
- Hidden rows are excluded from both XLSX and CSV output.
- XLSX exports rebuild every worksheet with only its unhidden rows.
- CSV exports the currently selected worksheet with only its unhidden rows.
- Original row order is preserved for all rows that remain.
- Header and detected introductory rows are preserved.
- Searching and sorting do not change what will be exported.

UNDO, REDO, AND SHORTCUTS
-------------------------
- Undo and Redo buttons restore previous hide and restore operations.
- Ctrl+Z undoes the last visibility change.
- Ctrl+Y or Ctrl+Shift+Z redoes a visibility change.
- Press / to focus the search box.
- Click a cell to select it, then use Ctrl+C to copy its value.

Large tables are displayed in manageable pages while filtering and exporting
continue to use the complete worksheet.

PRIVACY AND REQUIREMENTS
------------------------
Sheetflow processes the spreadsheet in your browser. The application does not
upload your file to a server.

The XLSX engine is loaded from the SheetJS CDN. If it is unavailable, CSV files
can still be imported and exported, but XLSX import and export will require a
working internet connection and a page reload.

RUNNING LOCALLY
---------------
1. Run start.cmd in this folder.
2. Open http://localhost:8001 in a browser.
3. Import your spreadsheet and begin organizing.

INSTALLING AS AN APP
--------------------
Sheetflow is a Progressive Web App. Open it through localhost or HTTPS, then
use the browser's Install app or Add to Home Screen option. The installed app
includes its own icon, opens without normal browser chrome, and caches the
Sheetflow interface for repeat visits. CSV workflows continue to work without
the network; XLSX support still needs the SheetJS engine from its CDN.

Sheetflow is a single-page application. The user interface, spreadsheet logic,
CSV parser, hiding tools, and export controls are contained in
stock-organizer.html.

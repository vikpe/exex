<div align="center">
    <h1>exex</h1>
    <p>
        <b>Extract data from Excel documents</b>
    </p>

[![PyPI version](https://badge.fury.io/py/exex.svg)](https://pypi.org/project/exex/)
![test](https://github.com/vikpe/exex/workflows/test/badge.svg?branch=master) [![codecov](https://codecov.io/gh/vikpe/exex/branch/master/graph/badge.svg)](https://codecov.io/gh/vikpe/exex)

<br>

</div>


## Installation
```sh
pip install exex
```

## Usage

![Sample Excel file](https://raw.githubusercontent.com/vikpe/exex/master/docs/sample_xlsx.png "Sample Excel file")

**Load Excel file**
```python
from openpyxl import load_workbook
from exex import parse

book = load_workbook("sample.xlsx") # load excel file
sheet = book.active # get active sheet
```

**Single cell by name**
```python
parse.values(sheet["A1"])
"name"
```

**Single cell by row/column number**
```python
parse.values(sheet.cell(row=1, column=1)) 
"name"
```
   
**Range of cells**
```python
parse.values(sheet["A1":"B2"])
[
  ["name", "abbreviation"],
  ["alpha", "a"],
]
```

**All cells**
```python              
parse.values(sheet.values)
[
  ["name", "abbreviation", "age"],
  ["alpha", "a", 1],
  ["beta", "b", 2],
  ["gamma", "g", 3],
]
```

**Row by number**
```python                  
parse.values(sheet[1])
["alpha", "a", 1]
```

**Range of rows**
```python           
parse.values(sheet[1:2])
[
  ["name", "abbreviation", "age"],
  ["alpha", "a", 1],
]
```

**Column by name**
```python            
parse.values(sheet["A"])
["name", "alpha", "beta", "gamma"]
```

**Rangge of columns**
```python
parse.values(sheet["A:B"])
[
  ["name", "alpha", "beta", "gamma"],
  ["abbreviation", "a", "b", "g"],
]
```

**Ways to access sheets**
```python
# Sheets
book.sheets[0]                # (sheet) sheet by index
book.sheets["prices"]         # (sheet) sheet by name
book.active                   # (sheet) active sheet

book.sheetnames               # (array) sheet names
```

## Development

**Setup**
```sh
poetry install
```

**Tests** (local Python version)
```sh
poetry run pytest
```

**Code formatting** (black)
```sh
poetry run black .
```

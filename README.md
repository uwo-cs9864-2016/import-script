# import-script

This is a script used for importing a set of rar'd CSV files into a `sqlite3` database. 

## Prequisites 

* Only works on Linux/OSX due to requiring `unrar`
* Data stored with the following format: `YYYY-MM-DD.rar/$ticker.csv`
  * The rar is assumed to have a full days worth of stocks
  * Each CSV file inside is a ticker, e.g. `aapl.csv` would be for Apple

## Running

Run `npm start -- YYYY-MM-DD --dir path/to/rar/files --db stock.db`. 

### Options

#### Required
 
* *Positional*: Date to import, format: `YYYY-MM-DD`
* `--dir`: Directory where `rar` files are stored
* `--db`: Name of `sqlite3` database

#### Available

* `--quiet`, `-q`: Quiet (default: `false`)
* `--clean-db`: `DROP` all tables within the database (if it exists) (default: `true`)
* `--nuke-db`: If the database file exists, delete it and recreate it (default: `false`)
* `--chunk-size`: How many tickers to process at a time before it is written to the `sqlite3` database (default: `500000`)
* `--log-level`: How much debug information is written (default: `info`)

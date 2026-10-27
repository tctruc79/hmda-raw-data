# Raw HMDA home purchase applications, 2018 to 2025

The raw data of the individual project *Which Mortgage Applications
Will Be Denied?* (Data Science and Applications, University of
Economics Ho Chi Minh City, October 2026): the 408 files downloaded
from the HMDA Data Browser, one per state and year, kept unchanged so
that the project can be rerun from the same files.

The files are in the release **v1** of this repository. Each one is
`hmda_<year>_<state>.csv.zip`, a zip that holds `hmda_<year>_<state>.csv`
exactly as it was downloaded (99 columns). In all: 40,553,705
applications, 15.62 GB as CSV, 2.21 GB zipped.

| Year | Files | Applications | CSV (GB) | Zipped (MB) |
|---|---|---|---|---|
| 2018 | 51 | 5,155,401 | 2.02 | 275.44 |
| 2019 | 51 | 5,298,812 | 2.08 | 285.88 |
| 2020 | 51 | 5,794,256 | 2.21 | 314.47 |
| 2021 | 51 | 6,285,542 | 2.41 | 349.03 |
| 2022 | 51 | 5,253,742 | 2.01 | 294.51 |
| 2023 | 51 | 4,202,333 | 1.61 | 234.44 |
| 2024 | 51 | 4,262,401 | 1.63 | 228.38 |
| 2025 | 51 | 4,301,218 | 1.64 | 231.45 |

`manifest.csv` lists every file with its year, state, number of
applications and sizes.

## Where the data come from

Home Mortgage Disclosure Act (HMDA) records published by the Federal
Financial Institutions Examination Council through the HMDA Data
Browser (https://ffiec.cfpb.gov/data-browser/). Each file was
downloaded on 19 October 2026 from

    https://ffiec.cfpb.gov/v2/data-browser-api/view/csv?states=<STATE>&years=<YEAR>&actions_taken=1,2,3&loan_purposes=1

for the 50 states and the District of Columbia and the years 2018 to
2025: home purchase loans (loan purpose 1) that reached a credit
decision, that is originated (1), approved but not taken (2) or denied
(3). HMDA data are a work of the US government, free to use and share;
they hold no names, addresses or account numbers. The HMDA Data Browser
remains the official source.

## Downloading

**Everything at once.** Two zips in release v1 hold all 408 CSV files:
`hmda_raw_2018_2021.zip` (1.22 GB, 204 files) and
`hmda_raw_2022_2025.zip` (0.99 GB, 204 files). One zip of all eight years
would be 2.21 GB, above GitHub's limit of 2 GB per file.

**One file.** Click it under **Assets** in release v1, or choose its year
and state in the Submitted materials tab of the project app
(https://hmda-triage.streamlit.app).

**With the GitHub command line tool:**

    gh release download v1 -R tctruc79/hmda-raw-data

## Checking a download

In the folder that holds the downloaded zips,

    shasum -a 256 -c --ignore-missing SHA256SUMS.txt

prints `OK` for each zip that is exactly the one published here
(`--ignore-missing` skips the files not downloaded). After unzipping,
`shasum -a 256 -c --ignore-missing SHA256SUMS_csv.txt` does the same for
the CSV files, which are byte for byte the files the HMDA Data Browser
returned.

## Cleaned data

The cleaned files, one Parquet file per year, are in
https://github.com/tctruc79/hmda-clean-data.

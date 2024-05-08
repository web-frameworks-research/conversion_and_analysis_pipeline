# Conversion and Analysis Pipeline for Project WebCensus

This repository contains all Jupyter notebooks used in the analysis and reporting for Project WebCensus. We used Kaggle's pipeline feature to connect multiple notebooks together by selecting a "previous" notebook's output data as a "current" notebook's input data.

Note that the datasets are not included in this GitHub repository due to size limitations; only the notebooks.

Here's a graph showing how the Kaggle notebooks and datasets used for this project are linked to one another:

```mermaid
graph TD
    D1["<b>Dataset: Website Framework Data (initial) <br> (original data from CrUX website)"]
    D1 --> N1["<b>1. aggregate-framework-data-into-sqlite-database.ipynb</b> <br> (converted the original data format, gzipped <br> sharded CSV files, to an SQLite database)"]
    N1 --> N2["<b>2. get-list-of-domain-names-from-sqlite-database.ipynb</b> <br> (extracted a list of domain names from the <br> original dataset, which proved to be easier <br> for some downstream tasks to consume)"]
    D2["<b>Dataset: Web Frameworks Scraper Data</b> <br> (contains scripts within web_framework_scraper repo) "] --> N3
    N3 --> N3
    N1 --> N3["<b>3. web-scraper.ipynb</b> <br> (main web scraping notebook)"]
    N2 --> N3
    N3 --> N4["<b>4. web-scraper-2-preliminary-data-processing.ipynb</b> <br> (preprocessing tasks)"]
    N4 --> N5["<b>5. assignment-2-statistical-analysis.ipynb</b> <br> (performed more preprocessing in preparation <br> for Assignment 2, such as joining the columns <br> in the original dataset with the ones <br> obtained from web scraping)"]
    N1 --> N5
    N5 --> N6["<b>6. final-project-checkpoint-2.ipynb</b> <br> (final submission for Checkpoint 2)"]
    N5 --> N7["<b>7. final-project-submission.ipynb</b> <br> (final submission for this project)"]
```
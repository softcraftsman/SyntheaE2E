# Medallion Architecture using Synapse for Synthea data
Using Synthea to create CSV files, we can simulate an EHR that is feeding data to the reporting and analysis system. This approach then will transform the data into a medallion archiecture by collecting the data in the bronze layer using Azure Data Factory.  We will then move the data into the Silver layer during a normalization and enrichment phase.  And finally, we will combine the data into presentation layers for the Gold layer.  This will then be consumed by the PowerBI reporting engine.

## Generate CSV patient files with Synthea
Using Synthea to create CSV files, we can simulate an EHR that is feeding data to the reporting and analysis system.  Synthea code can be found at https://github.com/synthetichealth/synthea.  We will be using the built jar file from the Releases section.

## Ingest raw data into Bronze layer
The Bronze layer is to aggregate multiple data feeds without translation.  We use Azure Data Factory to move the data from CSV files to Parquet tables.  This process compresses the data before it writes it and reduces the latency.

## Normalize and Enhance into the Silver layer
Using ADF Data Flows we normalize the fields and add new ones.  We also provide the equivalent syntax in a Jupyter notebook.

## Presentation views into the Gold Layer
The gold layer is also using ADF Data Factory to combine tables and reduce columns for presentation purposes.

## Power BI
The actual reports are created using the Serverless SQL engine of Synapse and sharing it with PowerBI.


# Open Fibre Data Standard - Sample Datasets

This is a collection of fibre optic network maps stored in the Open Fibre Data Standard (OFDS) format.  They are here for testing purpose and should not in any way be deemed authoritative.

## Workflow

The generate-pmtiles.yml GitHub Action workflow automatically generates a PMTiles file containing fiber network data organized by operator. It processes GeoJSON files from the repository's country/operator directory structure, combining both nodes and spans for each operator into a single consolidated layer. 

The workflow follows a predictable pattern: countries are represented by top-level directories, with each country containing subdirectories for different operators. For each operator, the workflow locates files containing "nodes" and "spans" in their filenames and assigns them to a layer named using the {country}_{operator} convention. The workflow then uses [Tippecanoe](https://github.com/felt/tippecanoe) to generate the PMTiles file with appropriate zoom levels and density settings, and uploads the result to Amazon S3 for hosting. S3 credentials are stored separately.
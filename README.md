# Sunbeam metaQUAST extension

This is a [metaQUAST](http://quast.sourceforge.net/metaquast) extension to the [Sunbeam pipeline](https://github.com/sunbeam-labs/sunbeam). 

 - `sbx_metaquast_env.yml` specifies the extension's dependencies, which is the QUAST software
 - `config.yml` contains configuration options (just the number of threads)
 - `sbx_metaquast.rules` contains the rules (logic/commands run) of the extension

## Installing the extension

Extension install is as simple as passing the extension's URL on GitHub to `sunbeam extend`:

    sunbeam extend https://github.com/zoey-rw/sbx_metaquast

Any user-modifiable parameters specified in `config.yml` are automatically added on `sunbeam init`. If you're installing an extension in a project where you already have a config file, run the following to add the options for your newly added extension to your config (the `-i` flag means in-place config file modification; remove the `-i` flag to see the new config in stdout):

    sunbeam config update -i sunbeam_config.yml

Installation instructions for older versions of Sunbeam are included at the end of this README.

## Running an extension

To run an extension, simply run Sunbeam as usual with your extension's target rule specified:

    sunbeam run --configfile=sunbeam_config.yml --use-conda metaquast

The `--use-conda` flag is required to let Snakemake know that you want to use the conda environment(s) included with your extension.

-------
    
## Installing an extension (legacy instructions for sunbeam <3.0)

Installing an extension is as simple as cloning (or moving) your extension directory into the sunbeam/extensions/ folder, installing requirements through Conda, and adding the new options to your existing configuration file: 

    git clone https://github.com/zoey-rw/sbx_metaquast/ sunbeam/extensions/sbx_metaquast
    cat sunbeam/extensions/sbx_metaquast/config.yml >> sunbeam_config.yml


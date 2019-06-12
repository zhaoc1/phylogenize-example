# Examples to run [Phylogenize](https://phylogenize.org/)

## Install Phylogenize package

Create the qiime2 Conda environment

```bash
wget https://data.qiime2.org/distro/core/qiime2-2019.4-py36-linux-conda.yml
conda env create -n qiime2-2019.4 --file qiime2-2019.4-py36-linux-conda.yml
```

- A few R packages installed through Conda

```bash
conda install -c r r-git2r
conda install -c bioconda bioconductor-biomformat
conda install -c conda-forge r-magick
conda install -c r r-shiny
```

- Follow steps from [Phylogenize](https://bitbucket.org/pbradz/phylogenize/src/master/)

```R
install.packages("BiocManager")
BiocManager::install(c("qvalue","biomformat","ggtree"))
install.packages("devtools")
devtools::install_bitbucket("pbradz/phylogenize/package/phylogenize")
```

### Fontconfig error: unable to match font pattern

If you see this error, probably gdtools is properlly installed, following the [steps](https://github.com/davidgohel/ggiraph/issues/69)

In a terminal, run the 3 following commands.

```bash
brew update
brew upgrade
brew reinsall cairo
```

Start a new R session and run

```R
devtools::install_github("davidgohel/gdtools") 
devtools::install_github("davidgohel/rvg")
devtools::install_github("davidgohel/ggiraph")
```

### Check for sys_fonts()

```bash
fc-list
```

If fc-list is not found on your system, install **fontconfig** package

```bash
sudo apt-get install fontconfig
```

Check the output of 

```R
gdtools::sys_fonts()
```

### AWS-specific

```bash
conda install -c conda-forge xorg-libxt
sudo apt install zlib
sudo apt show zlib1g
```

## Run phylogenize

```R
render.report(
    in_dir="/mnt/chunyu20TB/hmp_16s",
    biom_file="hmp-16s.biom",
    input_format="biom",
    type="16S",
    out_dir=file.path("/mnt/chunyu20TB/hmp_16s", "test9"),
    output_file="16S-results.html",
    which_phenotype="prevalence",
    which_envir="Stool",
    burst_dir="/mnt/chunyu20TB/bin/",
    ncl=4)
```



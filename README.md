# mpg-manufacturer-analysis

Do car manufacturers differ in city fuel economy once engine size and model year are accounted for? A mixed-effects
analysis of ggplot2's `mpg` data, written up as the paper
[MPG ~ Manufacturer, Analysis](https://www.alphaxiv.org/abs/2610.mpg-manufacturer-analysis) on alphaXiv.

```
index.qmd          the paper (R, knitr)
_quarto.yml        PDF format; renders to _output/mpg-manufacturer-analysis.pdf
references.bib     references
_freeze/           frozen results of the R code (tracked)
renv.lock          R package versions (renv)
_wide-tables.lua   fits wide tables to the page in the PDF
mpg.jpg            thumbnail
```

## Render

```bash
Rscript -e 'renv::restore()'                       # once: install the R packages in renv.lock
QUARTO_R=/opt/homebrew/bin/Rscript quarto render   # -> _output/mpg-manufacturer-analysis.pdf
```

The code draws an unseeded random sample for one table and bootstrap confidence intervals, so its results are
frozen in `_freeze/`: rendering reuses them and reproduces the published paper exactly. Editing a code chunk
re-runs the code, which redraws those random parts.

Data: `mpg` from the ggplot2 R package (EPA fuel economy data for 38 car models, 1999 and 2008).

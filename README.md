---
title: "dplyrStarter"
author: "tidyverse"
output: rmarkdown::github_document
---

# dplyr <a href='https://dplyr.tidyverse.org'><img src='man/figures/logo.png' align="right" height="139" /></a>

<!-- badges: start -->
[![CRAN status](https://www.r-pkg.org/badges/version/dplyr)](https://cran.r-project.org/package=dplyr)
[![R build status](https://github.com/tidyverse/dplyr/workflows/R-CMD-check/badge.svg)](https://github.com/tidyverse/dplyr/actions?workflow=R-CMD-check)
[![Codecov test coverage](https://codecov.io/gh/tidyverse/dplyr/branch/main/graph/badge.svg)](https://app.codecov.io/gh/tidyverse/dplyr?branch=main)
<!-- badges: end -->

## Overview

dplyr is a grammar of data manipulation, providing a consistent set of verbs that help you solve the most common data manipulation challenges:

* `mutate()` adds new variables that are functions of existing variables
* `select()` picks variables based on their names.
* `filter()` picks cases based on their values.
* `summarise()` reduces multiple values down to a single summary.
* `arrange()` changes the ordering of the rows.

These all combine naturally with `group_by()` which allows you to perform any operation "by group". You can learn more about them in `vignette("dplyr")`. As well as these single-table verbs, dplyr also provides a variety of two-table verbs, which you can learn about in `vignette("two-table")`.

If you are new to dplyr, the best place to start is the [data transformation chapter](https://r4ds.had.co.nz/transform.html) in R for data science.

## Backends

In addition to data frames/tibbles, dplyr makes working with other computational backends accessible and efficient. Below is a list of alternative backends:

- [dtplyr](https://dtplyr.tidyverse.org/): for large, in-memory datasets. 
  Translates your dplyr code to high performance 
  [data.table](https://rdatatable.gitlab.io/data.table/) code.

- [dbplyr](https://dbplyr.tidyverse.org/): for data stored in a relational 
  database. Translates your dplyr code to SQL.

- [sparklyr](https://spark.rstudio.com): for very large datasets stored in 
  [Apache Spark](https://spark.apache.org).

## Installation

```{r, eval = FALSE}
# The easiest way to get dplyr is to install the whole tidyverse:
install.packages("tidyverse")
# Alternatively, install just dplyr:
install.packages("dplyr")
```

### Development version

To get a bug fix or to use a feature from the development version, you can install 
the development version of dplyr from GitHub.

```{r, eval = FALSE}
# install.packages("devtools")
devtools::install_github("tidyverse/dplyr")
```

## Cheat Sheet

<a href="https://github.com/rstudio/cheatsheets/blob/main/data-transformation.pdf"><img src="https://raw.githubusercontent.com/rstudio/cheatsheets/main/pngs/thumbnails/data-transformation-cheatsheet-thumbs.png" width="630" height="252"/></a>  

## Usage

```{r, message = FALSE}
library(dplyr)
starwars %>% 
  filter(species == "Droid")
starwars %>% 
  select(name, ends_with("color"))
starwars %>% 
  mutate(name, bmi = mass / ((height / 100)  ^ 2)) %>%
  select(name:mass, bmi)
starwars %>% 
  arrange(desc(mass))
starwars %>%
  group_by(species) %>%
  summarise(
    n = n(),
    mass = mean(mass, na.rm = TRUE)
  ) %>%
  filter(
    n > 1,
    mass > 50
  )
```

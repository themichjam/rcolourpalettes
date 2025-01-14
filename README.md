# r_colour_palettes

Different custom colour palettes for R visulisations. Mostly based on Horror, SciFi and Rock music. Updated list of palettes below. Package in development.


### Contents:
  - [The Exorcist](#theexorcistpalette)
  - [Jaws](#thejawspalette)
  - [Alien](#alienpalette)
  - [Tutorial: How To](#tutorial)
 
 
## The Exorcist Palette

![Exorcist](exorcist/images/exorcistpalette.png)

<font size="1"> Picture: the original The Exorcist movie poster.</font>

## Jaws Palette

![Jaws](jaws/images/jawspalettepic.png)

<font size="1"> Picture: the original Jaws movie poster.</font>

## Alien Palette

![Jaws](alien/images/alienpalettepic.png)

<font size="1"> Picture: the original Jaws movie poster.</font>


## Tutorial

## Extracting colors from images with the colorfindr package

This is a short tutorial that will get you started with building your
very own custom color palette with the {colorfindr} package by David
Zumbach, and use it in a ggplot. For this we will
be using the Palmer Penguins package by Allison Horst, Alison Hill and Kristen Gorman. 
There are many, many color palettes already out there, but what I love about colorfindr is
that it is 100% customizable. You can choose to extract however many
colors you want and use any favorite film, TV show or art work as
inspiration. Of course, I chose horror!

### Step 1: Install colorfindr

``` r
# install.packages("colorfindr") 
# install.packages("tidyverse") 
# install.packages("palmerpenguins")
library(colorfindr) # extracts colors from images
library(tidyverse) # tidy data wrangling & plotting
```

### Step 2: Extract colors from images

``` r
# Get colors and create a palette with n = 5
get_colors("images/exorcistposter.jpg") %>% # you can reference a local file on your computer or a jpg web address
  make_palette(n = 5) # here we extract 5 colors
```

You can play around with how many colors you extract - this will depend
on what your data looks like. Do you want to show a few different
categories or continuous values? **Tip**: For very expressive color
palettes, I would pick images with strong, vibrant colors.


If you’ve decided that you want 3 different colors, save your new
palette to a so-called character vector. You can also ‘set a seed’,
which will ensure that you get the same colors every time you run your
script.

``` r
# Use your favorite magic number to set a seed:
# set.seed(42)
TEP <- get_colors("images/exorcistposter.jpg") %>%
  make_palette(n = 5)
```

### Step 3: Use your new palette

From this:

``` r
library(palmerpenguins) # get the penguin data
penguins %>% # feed ggplot the data
  ggplot(aes(flipper_length_mm, fill = species)) + # we want to investigate the flipper length of our penguin friends
  geom_density(alpha = 0.8, color =NA)+ # specify how you want to display the data
  theme_minimal() # pick a theme
```

To this 🔥:

``` r
penguins %>%
  ggplot(aes(flipper_length_mm, fill = species)) +
  geom_density(alpha = 0.8, color =NA)+
  scale_fill_manual(values = TEP)+
  theme_minimal()
```

### Get inspired by the cool palettes other folks made with colorfindr

[Kelly Cotton](https://twitter.com/kllycttn) built a new package of New York-inspired palettes: https://github.com/kellycotton/nycpalettes
![](https://raw.githubusercontent.com/kellycotton/nycpalettes/master/man/figures/README-Sunset2-1.png)

[Ben Stanley](https://twitter.com/BDStanley) made a palette for Kieslowski's "Dekalog":https://twitter.com/BDStanley/status/1307605257019629570 
![](https://pbs.twimg.com/media/EiWL5Y7WAAA_9Ee?format=png&name=4096x4096)

[Lydia Hopper](https://twitter.com/LydiaMHopper) made a palette inspired by Japanese macaques: https://twitter.com/LydiaMHopper/status/1308403623592943616
![](https://pbs.twimg.com/media/Eihh7cBX0AMhJKo?format=jpg&name=medium)

[Kaylea](https://twitter.com/KayleaHaynes) was inspired by #TidyTuesday and looked at reasons for expedition terminations: https://twitter.com/KayleaHaynes/status/1308799804357709825  
![](https://pbs.twimg.com/media/EinIs0ZXYAACvs1?format=jpg&name=4096x4096)  

[John MacKintosh](https://twitter.com/_johnmackintosh) made his own "Metallicart" package with album covers of Metallica as inspiration: https://github.com/johnmackintosh/metallicaRt  
![](https://pbs.twimg.com/media/EinifjVWoAI2jgv?format=png&name=900x900)  

[Kelly Morrow McCarthy](https://twitter.com/KellyMM_neuro) was inspired by an abstract photo: https://twitter.com/KellyMM_neuro/status/1308763829095063560  
![](https://pbs.twimg.com/media/Eimpk-HWAAMLjgJ?format=jpg&name=medium)  



### References.  
* Horst AM, Hill AP, Gorman KB (2020). palmerpenguins: Palmer Archipelago (Antarctica) penguin data. R package version 0.1.0. https://allisonhorst.github.io/palmerpenguins/. doi: 10.5281/zenodo.3960218.  
* Zumbach, D. colorfindr. R package version 0.1.3. https://github.com/zumbov2/colorfindr.  

* 200 Best Horror Movies of All Time. Rotten Tomatoes. https://editorial.rottentomatoes.com/guide/best-horror-movies-of-all-time/

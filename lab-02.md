Lab 02 - Plastic waste
================
Saima Arina
01/22/2026

## Load packages and data

``` r
library(tidyverse) 
```

``` r
plastic_waste <- read.csv("data/plastic-waste.csv")
```

## Exercises

### Exercise 1

In terms of their plastic waste per capita, it seems that North America
has the highest, with the Trinidad and Tobago outlier of over 3.5
kg/person and also a skew towards higher numbers. Oceania and South
America share similar distributions. Africa seems to have the lowest,
with most countries below 0.2 kg/person. Asia seems to have a skew
towards the right.

``` r
ggplot(data = plastic_waste, mapping = aes (x = plastic_waste_per_cap)) + geom_histogram (binwidth = 0.1) +
facet_wrap(~ continent)
```

    ## Warning: Removed 51 rows containing non-finite outside the scale range
    ## (`stat_bin()`).

![](lab-02_files/figure-gfm/plastic-waste-continent-1.png)<!-- -->

### Exercise 2

``` r
ggplot(
  data = plastic_waste,
  mapping = aes(
    x = plastic_waste_per_cap,
    color = continent,
    fill = continent,
  )
) +
  geom_density(alpha = 0.175)
```

    ## Warning: Removed 51 rows containing non-finite outside the scale range
    ## (`stat_density()`).

![](lab-02_files/figure-gfm/plastic-waste-density-1.png)<!-- -->

The color and fill of the curves were defined by mapping aesthetics
because if the info is to be in the legend, it must be a part of this
layer. Also, it allows the colors to scale for each group. The alpha
level is defined as a characteristic of the plotting geom because it is
a element universally applied to all of the groups rather than
differently for them individually.

### Exercise 3

Violin plots are capable of revealing the shape of the distribution,
including peaks and skewness, while box plots provide more information
on quartiles and extreme outliers.

``` r
ggplot(
  data = plastic_waste,
  mapping = aes(
    x = continent,
    y = plastic_waste_per_cap
  )
) +
  geom_boxplot()
```

    ## Warning: Removed 51 rows containing non-finite outside the scale range
    ## (`stat_boxplot()`).

![](lab-02_files/figure-gfm/plastic-waste-violin-1.png)<!-- -->

``` r
ggplot(
  data = plastic_waste,
  mapping = aes(
    x = continent,
    y = plastic_waste_per_cap
    
  )
) +
  geom_violin()
```

    ## Warning: Removed 51 rows containing non-finite outside the scale range
    ## (`stat_ydensity()`).

![](lab-02_files/figure-gfm/unnamed-chunk-1-1.png)<!-- -->

### Exercise 4

There is a pretty visible positive linear relationship where higher
total plastic waste per capita is associated with higher amounts of
mismanaged plastic waste per capita, and most points are clustered along
a line that is upwards and there are some high outliers. In terms of
continent, all of the colors seem to flow the same positive trend, with
North America showing prominently high-value outliers. I would say for
the last two plots, that plastic waste per capita and total population
seem to be more strongly linearly associated because more of the data
points are clustered together in the same area while the other plot
measuring coastal population has a greater numbers of outliers and
slightly more spread.

``` r
ggplot(data = plastic_waste,
       mapping = aes(x = plastic_waste_per_cap,  y = mismanaged_plastic_waste_per_cap
                
                     )) +
  geom_point() 
```

    ## Warning: Removed 51 rows containing missing values or values outside the scale range
    ## (`geom_point()`).

![](lab-02_files/figure-gfm/plastic-waste-mismanaged-1.png)<!-- -->

``` r
ggplot(data = plastic_waste,
       mapping = aes(x = plastic_waste_per_cap,  y = mismanaged_plastic_waste_per_cap,
                     color = continent
                     )) +
  geom_point() 
```

    ## Warning: Removed 51 rows containing missing values or values outside the scale range
    ## (`geom_point()`).

![](lab-02_files/figure-gfm/plastic-waste-mismanaged-continent-1.png)<!-- -->

``` r
ggplot(data = plastic_waste, 
       mapping = aes(x = plastic_waste_per_cap, y = total_pop)) + geom_point ()
```

    ## Warning: Removed 61 rows containing missing values or values outside the scale range
    ## (`geom_point()`).

![](lab-02_files/figure-gfm/plastic-waste-population-total-1.png)<!-- -->

``` r
ggplot(data = plastic_waste, 
       mapping = aes (x = plastic_waste_per_cap, y = coastal_pop)) + geom_point ()
```

    ## Warning: Removed 51 rows containing missing values or values outside the scale range
    ## (`geom_point()`).

![](lab-02_files/figure-gfm/plastic-waste-population-coastal-1.png)<!-- -->

### Exercise 5

Remove this text, and add your answer for Exercise 5 here.

``` r
# insert code here
```

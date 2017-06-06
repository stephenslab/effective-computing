# Adding color to plots in R

The default colors in R (e.g., ggplot2) are not great, and indeed
there are much better coloring schemes. This is one that is intended
to be more visually distinguishable for people affected by color
blindness:

```R
colors <- c("#E69F00","#56B4E9","#009E73","#F0E442",
            "#0072B2","#D55E00","#CC79A7")
```

These colors are based on
[this paper](http://dx.doi.org/10.1038/nmeth.1618). See also
[here](http://www.cookbook-r.com/Graphs/Colors_(ggplot2)).

Here is a short R script demonstrating how to use it in ggplot2:

```
library(ggplot2)
colors <- c("#E69F00","#56B4E9","#009E73","#F0E442",
            "#0072B2","#D55E00","#CC79A7")
data(iris)
iris <- transform(iris,Petal.Length = cut(Petal.Length,breaks = 0:7))
print(ggplot(iris,aes(x = Sepal.Length,y = Sepal.Width,col = Petal.Length)) +
      geom_point(size = 2) +
      scale_color_manual(values = colors) +
      theme_minimal())
```


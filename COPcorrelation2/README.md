
[<img src="https://github.com/QuantLet/Styleguide-and-FAQ/blob/master/pictures/banner.png" width="880" alt="Visit QuantNet">](http://quantlet.de/index.php?p=info)

## [<img src="https://github.com/QuantLet/Styleguide-and-Validation-procedure/blob/master/pictures/qloqo.png" alt="Visit QuantNet">](http://quantlet.de/) **COPcorrelation2**[<img src="https://github.com/QuantLet/Styleguide-and-Validation-procedure/blob/master/pictures/QN2.png" width="60" alt="Visit QuantNet 2.0">](http://quantlet.de/d3/ia)

```yaml
Name of Quantlet: COPcorrelation2
 
Published in: Copulae

Description: 'COPcorrelation2 gives a plot of 100 scatter points generated 
respectively by uniform distribution and normal distribution with a drift 
generated by the aforementioned uniform distribution. Also the three 
different correlations are computed, the correlations of Pearson, Kendall
and Spearman.'
  
Keywords: correlation, distribution, normal, scatterplot, uniform
     
See also: COPcorrelation2, MMSTATscatterplot

Author: Ostap Okhrin, Yafei Xu

Submitted: Mon, October 20 2014 by Felix Jung

```

![Picture1](Correlation2.png)

```r
rm(list = ls(all = TRUE))
# set the parameters and draw samples
n  = 100
x  = runif(min = -1, max = 1, n) # draw 100 random numbers from a uniform CDF
y  = rnorm(n, mean = 0, sd = 0.1) + x 
x  = c(x, 1.2)
y  = c(y, 10)
b1 = var(x, y) / var(x)
b0 = mean(y) - b1 * mean(x)
# do the right scatter plot
plot(x, y, type = "p", pch = 19, col = "red3")
lines(x = c(-1, 1), y = c(b0 - b1, b0 + b1), lwd = 2, col = "blue3")
abline(a = 0, b = 0, v = seq(-1, 1, by = 0.25), h = seq(0, 10, by = 2),
       col = "gray", lty = 3)
# compute correlations of Pearson, Kendall and Spearman
print(cor(x, y))
print(cor(x, y, method = "kendall"))
print(cor(x, y, method = "spearman"))
```

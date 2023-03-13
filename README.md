# Assignment9
## Sriya Reddy

For this assignment, we are required to download a dataset and create plots using three different packages - Base R, lattice and ggplot. 
First, I installed the required packages with:

```
> install.packages("ggplot2")
```

The other two are already installed. I imported the libraries with:

```
> library("ggplot2")
> library("lattice")
```

I now downloaded the `Fatalities.csv` dataset using the provided link. This dataset contains information of all the fatalities in different states in the years 1982-1988, along with information about the drivers and the population. I loaded the downloaded dataset from my Downloads folder using:

```
> fatalities <- read.csv("./Downloads/Fatalities.csv")
```

Displaying the first 5 rows of the data, 

```
> head(fatalities, 5)
  X state year spirits unemp   income   emppop  beertax baptist  mormon drinkage
1 1    al 1982    1.37  14.4 10544.15 50.69204 1.539379 30.3557 0.32829    19.00
2 2    al 1983    1.36  13.7 10732.80 52.14703 1.788991 30.3336 0.34341    19.00
3 3    al 1984    1.32  11.1 11108.79 54.16809 1.714286 30.3115 0.35924    19.00
4 4    al 1985    1.28   8.9 11332.63 55.27114 1.652542 30.2895 0.37579    19.67
5 5    al 1986    1.23   9.8 11661.51 56.51450 1.609907 30.2674 0.39311    21.00
      dry youngdrivers    miles breath jail service fatal nfatal sfatal
1 25.0063     0.211572 7233.887     no   no      no   839    146     99
2 22.9942     0.210768 7836.348     no   no      no   930    154     98
3 24.0426     0.211484 8262.990     no   no      no   932    165     94
4 23.6339     0.211140 8726.917     no   no      no   882    146     98
5 23.4647     0.213400 8952.854     no   no      no  1081    172    119
  fatal1517 nfatal1517 fatal1820 nfatal1820 fatal2124 nfatal2124  afatal     pop
1        53          9        99         34       120         32 309.438 3942002
2        71          8       108         26       124         35 341.834 3960008
3        49          7       103         25       118         34 304.872 3988992
4        66          9       100         23       114         45 276.742 4021008
5        82         10       120         23       119         29 360.716 4049994
   pop1517  pop1820  pop2124 milestot unempus emppopus         gsp
1 208999.6 221553.4 290000.1    28516     9.7     57.8 -0.02212476
2 202000.1 219125.5 290000.2    31032     9.6     57.9  0.04655825
3 197000.0 216724.1 288000.2    32961     7.5     59.5  0.06279784
4 194999.7 214349.0 284000.3    35091     7.2     60.1  0.02748997
5 203999.9 212000.0 263000.3    36259     7.0     60.7  0.03214295
```

Now, I chose to plot the data for Florida state and hence I defined a new variable, `florida`, as:

```
> florida <- fatalities[50:56,]
> florida
    X state year spirits unemp   income   emppop  beertax baptist mormon
50 50    fl 1982    2.51   8.2 13502.39 53.48780 1.073986  9.1526    0.4
51 51    fl 1983    2.46   8.6 13924.31 53.72708 1.170413  8.9367    0.4
52 52    fl 1984    2.35   6.3 14307.69 55.62103 1.186813  8.7260    0.4
53 53    fl 1985    2.27   6.0 14760.59 56.36853 1.144068  8.5202    0.4
54 54    fl 1986    2.24   5.7 15102.17 57.44054 1.114551  8.3193    0.4
55 55    fl 1987    2.17   5.3 15584.00 58.94335 1.080000  8.1231    0.4
56 56    fl 1988    2.08   5.0 15979.79 59.79093 1.039461  7.9316    0.4
   drinkage dry youngdrivers    miles breath jail service fatal nfatal sfatal
50       19   0     0.181476 7587.130    yes   no     yes  2653    587    282
51       19   0     0.177945 7604.254    yes   no     yes  2686    562    291
52       19   0     0.178720 7735.305    yes   no     yes  2814    566    311
53       20   0     0.170072 7747.311    yes   no     yes  2832    490    254
54       21   0     0.162555 7768.756    yes   no     yes  2830    530    296
55       21   0     0.161258 7788.331    yes   no     yes  2839    493    262
56       21   0     0.157563 8538.230    yes   no     yes  3078    573    315
   fatal1517 nfatal1517 fatal1820 nfatal1820 fatal2124 nfatal2124 afatal
50       148         35       259         86       350        123 810.76
51       132         30       274         92       317        110 963.90
52       150         29       270         88       344        129 744.38
53       146         24       239         79       341        101 690.20
54       173         39       263         92       347         94 806.84
55       166         32       227         75       326         94 778.97
56       184         42       278         73       382        145 794.75
        pop  pop1517  pop1820  pop2124 milestot unempus emppopus         gsp
50 10478007 476999.3 492108.4 687999.9    79498     9.7     57.8 0.005385397
51 10753980 467000.4 497250.2 701000.2    81776     9.6     57.9 0.077084795
52 11049985 459000.6 502445.7 713000.7    85475     7.5     59.5 0.080842420
53 11366008 456999.8 507695.4 718999.8    88056     7.2     60.1 0.059289411
54 11694022 474999.4 513000.0 670999.5    90848     7.0     60.7 0.053569589
55 12022987 483000.4 512994.3 670000.2    93639     6.2     61.5 0.062531143
56 12334992 477000.3 492000.6 698999.9   105319     5.5     62.3 0.050752144
```

I now chose to plot a bar chartof the number of fatalities (column: `fatal`) each year (column: `year`) using the three methods as instructed. 

**1) Base R**

Using just Base R, with no package, I used the `barplot()` command:

```
> barplot(florida$fatal, xlab='Year', ylab='Fatalities', main='Fatalities per year in Florida', names.arg = florida$year, col='purple')
```

Here:

1) `florida$fatal` provides the vector of heights for the bars
2) `xlab='Year'` provides the x-axis label
3) `ylab='Fatalities'` provides the y-axis label
4) `main='Fatalities per year in Florida'` provides the figure title
5) `names.arg = florida$year` provides the bar labels
6) `col='purple'` provides the color for the bars

The obtained chart is shown below. 

![](https://github.com/venatisriya/assignment9/blob/main/RplotR.png)

This implementation was easy to use and customize. I found it to be very interesting.

**2) Lattice**

Using the Lattice package, I used the `barchart()` command:

```
> barchart(florida$fatal~florida$year, florida, main='Fatalities per year in Florida', xlab='Year', ylab='Fatalities', horiz=FALSE, scales=list(florida$year))
```

Here:

1) `florida$fatal~florida$year` provides the vectors to be used for the y-axis and the x-axis respectively
2) `florida` provides the data frame to be used
3) `main='Fatalities per year in Florida'` provides the figure title
4) `xlab='Year'` provides the x-axis label
5) `ylab='Fatalities'` provides the y-axis label
6) `horiz=FALSE` specifies that we need a verrtical bar chart
7) `scales=list(florida$year)` provides the list of bar labels

The obtained chart is shown below. 

![](https://github.com/venatisriya/assignment9/blob/main/Rplotlattice.png)

I found this implementation to be the toughest of the three. This was because the arguments to the function were not intuitive and I had to iterate multiple times, experimenting with different methods of providing the arguments to obtain the plot in the fashion that I wanted. Also, it took me some time to figure out the `horiz` argument to make the plot vertical. Though interesting, I found this package to be difficult to use. 

**3) ggplot**

Using the ggplot package, I used the `ggplot()` command:

```
> ggplot(florida, aes(year, fatal))+ geom_col(fill = rainbow(7)) + scale_x_continuous(breaks=florida$year, labels=florida$year) + labs(title = "Fatalities per year in Florida")
```

Here:

1) `florida` provides the data frame to be used
2) `aes(year, fatal))` provides the columns to be used
3) `geom_col(fill = rainbow(7))` provides the color scheme to be used
4) `scale_x_continuous(breaks=florida$year, labels=florida$year)` provides labels for the bars on the x-axis
5) `labs(title = "Fatalities per year in Florida")` provides the figure title

The obtained chart is shown below. 

![](https://github.com/venatisriya/assignment9/blob/main/Rplotggplot.png)

I found this implementation to be the best of the three. Though it took me some time to understand the arguments, it was quite straightforward after that. The only trouble I had was with providing the bar labels, whiich need to be defined as discrete or continuous. 

Overall, I found the output provided by ggplot to be the best looking of the three. 
This exercise was very interesting and helped me learn about the usage of the different visualization packages in R. I also explored and found other plot commands, which was very interesting. 








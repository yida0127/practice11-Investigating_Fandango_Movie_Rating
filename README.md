# Guided Project - Investigating_Fandango_Movie_Rating

In October 2015, a data journalist named Walt Hickey analyzed movie ratings data and found strong evidence to suggest that 
Fandango's rating system was biased and dishonest ([Fandango](https://www.fandango.com/) is an online movie ratings aggregator). 
He published his analysis [in this article](https://fivethirtyeight.com/features/fandango-movies-ratings/) — a great piece of data journalism that's totally worth reading.

Fandango displays a 5-star rating system on their website, where the minimum rating is 0 stars and the maximum is 5 stars.

![fandango](https://s3.amazonaws.com/dq-content/288/s1gp_fdg_stars.png)

Hickey found that there's a significant discrepancy between the number of stars displayed to users and the actual rating, 
which he was able to find in the HTML of the page. He was able to find that:

* The actual rating was almost always rounded up to the nearest half-star. For instance, a 4.1 movie would be rounded off to 4.5 stars, not to 4 stars, as you may expect.
* In the case of 8% of the ratings analyzed, the rounding up was done to the nearest whole star. For instance, a 4.5 rating would be rounded off to 5 stars.
* For one movie rating, the rounding off was completely bizarre: from a rating of 4 in the HTML of the page to a displayed rating of 5 stars.

![pic](https://s3.amazonaws.com/dq-content/288/s1gp_actual_vs_displayed.png)

Source: [FiveThirtyEight](https://fivethirtyeight.com/features/fandango-movies-ratings/)

The two distributions above are displayed using a simple line plot, which is also a valid way to show the shape of a distribution. 
The variable being examined is movie rating, and for each unique rating we can see its relative frequency (percentage) on the y-axis of the graph. 
When an analysis report is intended for large audiences, relative frequencies (especially percentages) are preferred over absolute frequencies.

Both distributions above are strongly left skewed, suggesting that movie ratings on Fandango are generally high or very high. 
We can see there's no rating under 2 stars in the sample Hickey analyzed. The distribution of displayed ratings is clearly 
shifted to the right compared to the actual rating distribution, suggesting strongly that Fandango inflates the ratings under the hood.

Fandango's officials replied that the biased rounding off was caused by a bug in their system rather than being intentional, 
and they promised to fix the bug as soon as possible. Presumably, this has already happened, although we can't tell for sure 
since the actual rating value doesn't seem to be displayed anymore in the pages' HTML.

In this project, we'll analyze more recent movie ratings data to determine <b>whether there has been any change in Fandango's 
rating system after Hickey's analysis.</b>

We'll use two datasets in different periods of time:
* Walt Hickey made the data he analyzed publicly available [on GitHub](https://github.com/fivethirtyeight/data/tree/master/fandango). We'll use the data he collected to analyze the characteristics of Fandango's rating system previous to his analysis.

* One of Dataquest's team members collected movie ratings data for movies released in 2016 and 2017. The data is publicly available [on GitHub](https://github.com/mircealex/Movie_ratings_2016_17) and we'll use it to analyze the rating system's characteristics after Hickey's analysis.

---
title: "Basic Math Question - Rate of Chnage"
date: 2010-07-19
forum: The Cafe
---

### Post by SNYP40A1 on 2010-07-19
Say I have two functions that I expect should correlate with time.  Meaning that as one function increases in value with time, the other function should increase in value with time as well.  A simple example of this might be the price of coffee vs. price of sugar.  One way to quantify this rate of change is to take a price change ratio at two points in time.  Such as:

( C(t2) - C(t1) ) / ( S(t2) - S(t1) ) 

Problem is that if sugar (in the denominator) happened to have the same price at t2 and t1, the ratio is infinite.  Does anyone know of a better way of comparing the relative rate of change between two discrete-valued functions?  Or anyone know of a better place to ask this question?

---

### Post by pmlxuser on 2010-07-19
i would if i were you. start with a finction to check that S (t1) and S(t2) !=

ie
if  
S(t1)=S(t2) { skip /or somthing)

else
( C(t2) - C(t1) ) / ( S(t2) - S(t1) )

think of if the price is the same  you function should have a means of determining somthing i don't know what

---

### Post by ad_267 on 2010-07-19
Yep the Covariance is exactly what you're after: [http://en.wikipedia.org/wiki/Covariance](http://en.wikipedia.org/wiki/Covariance)

Edit: numpy.cov(a,b)[0,1] in python will give you the covariance between two arrays a and b.

---

### Post by Sporkman on 2010-07-19
If you're doing things analytically, you'd want to compare the first derivatives of the functions at the given time.

---

### Post by rewyllys on 2010-07-19
> **SNYP40A1 said:**
> . . . . Does anyone know of a better way of comparing the relative rate of change between two discrete-valued functions?  Or anyone know of a better place to ask this question?

I think that you'd find the Pearson partial correlation coefficient ([http://en.wikipedia.org/wiki/Partial_correlation](http://en.wikipedia.org/wiki/Partial_correlation)) to be what you're looking for. 

Yes, technically, the PPCC requires the variables to be continuous, but the PPCC is widely used with discrete variables like costs in dollars, etc.  

One rationale for accepting such uses of the PPCC is the pragmatic fact that, in the real world, we can never measure values of continuous variables except by observations that are necessarily expressed as numbers with a finite number of decimal digits.  That is to say, we assume that cost is a continuous variable with which we have to work in terms of dollars (or other currencies) expressed to 2 (or 3, or 4, or . . .) decimal digits.

---

### Post by Shining Arcanine on 2010-07-19
> **Sporkman said:**
> If you're doing things analytically, you'd want to compare the first derivatives of the functions at the given time.

That was my first thought, but unfortunately, he is using discrete valued functions. He cannot do things analytically unless he can find a polynomial that fits his data. It is possible, but finding one will likely be difficult to do.

---

### Post by SNYP40A1 on 2010-07-19
> **Shining Arcanine said:**
> That was my first thought, but unfortunately, he is using discrete valued functions. He cannot do things analytically unless he can find a polynomial that fits his data. It is possible, but finding one will likely be difficult to do.

Yup, I don't have the polynomial.  Taking the ratios of slopes is essentially a difference equation which is the discrete analog of derivatives for continuous functions.

---

### Post by McRat on 2010-07-19
Seems all you need to do is express the values as just standard unit indexes.

That is, no change = 1
double change = 2
half change = 0.5



So you use:

 (Cost2011/Cost2010)  /   (Price2011/Price2010)

Or am I not understanding right?

---

### Post by 3Miro on 2010-07-19
When S(t1) and S(t2) are the same, you don't get infinity, but "undefined". You will also run into trouble if S(t1) is close to S(t2) and then the answer will probably diverge.

I am not sure if this will help, but wouldn't it make more sense to show that the "rate of increase of price of coffee is proportional to the rate of increase of the price of sugar". Then you will work with 
```
( C(t2) - C(t1) ) = K ( S(t2) - S(t1) )
```
and try to see what K is. Note that in this case you don't get anything undefined.

However, you always have other factors influencing the problem. To correctly determine statistical information form a sample, you will probably need "covariance". Look it up, it is somewhat involved.

---

### Post by SNYP40A1 on 2010-07-19
Update: A thought a little longer about my question below.  I think the answer is that it depends.  If I draw two lines on a blank piece of paper and they are in the same quadrant, but no scale is provided, the slope and therefore relative change cannot be determined.  All one could tell is whether the represented functions are increasing or decreasing together.  However, if I know that the two functions do correlate very closely 90% - 99% of the time, then I can use the initial value of the known function to guesstimate the initial value of the unknown function (which is initialized to 0 and represents a count).  Question is, is there a better method to determine relative change between two time series where the initial value of one time series is unknown (initialized to 0)?

Percent change would be the best approach.  However, for my problem, the initial value is unknown and only the relative changes in quantity from one step to the next are known (basically both variables are initialized to 0 and I am interested in the relative changes in value during the sampling window).  The problem is that the initial or starting condition determines the % change.  For example, if I am traveling 100 mph, then a 1 mph increase in velocity is not much.  However, if I am traveling 1 mph, then a 1 mph increase in velocity is a lot.  Is there a way to solve this problem if I only know the initial value for one of the variables, but not both?

---

### Post by ad_267 on 2010-07-20
Edit: Nevermind, after re-reading your original post it seems like you're not after the covariance but rather a measure of how much one variable changes with respect to another. The covariance would tell you how closely those variables are related.

---

### Post by SNYP40A1 on 2010-07-20
Interesting post related to this discussion:

[http://blog.bissantz.com/shocking-time-series](http://blog.bissantz.com/shocking-time-series)

I've found that what I'm really looking for is found inside a field of study called "Time Series Semblance Analysis".  There are a few Matlab packages for this based on wavelets.

To learn more on this topic, I recommend a book Conceptual Wavelets by Dr. Lee Fugal.

---


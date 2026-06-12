---
title: "MS Excel miscalculating values?"
date: 2008-03-07
forum: Windows
---

### Post by Erdaron on 2008-03-07
I've been working on some Python code to calculate basic statistical values, and I decided to check accuracy of my functions against Excel. This surprised me, because we disagreed. Then I checked with MathCad 14.

Results for standard deviation:

Data set: [1,2,3,4,5,6,7,8,9,10]
Me and MathCad: 2.872
Excel: 3.028

Data set: [1,2...999]
Me and MathCad: 288.675
Excel: 288.531

Mean seems to be right on, variance is similarly incorrect.

Seems that Excel is using something to approximate the value instead of using an exact expression.

This is using Excel 2003, Student and Teacher. It's a legit copy, running on legit Windows.

Has anyone else noticed something like this?

---

### Post by LaRoza on 2008-03-07
I have heard and seen Excel bugs, so I am not surprised.

Try it in calc, you never know.

---

### Post by Whiffle on 2008-03-07
My HP50g says standard deviation is 3.02765..., octave says 3.0277.  

For the second set, octave says 288.53

something tells me theres more than one way to do this.


EDIT:

Also, STDDEVP command in excel 2003 gives 2.8722.

---

### Post by tgalati4 on 2008-03-07
Gnumeric shows the standard deviation as: 3.02765035409749 for 1 to 10

For 1 to 999, it crashed.

Just kidding.  Standard Deviation:  288.53076092507

I though there were two ways to calculate:  One for small population (<28) and one for large.  I would have to crack a math text.

---

### Post by Flying caveman on 2008-03-07
decimal precision problem  ?????

---

### Post by Erdaron on 2008-03-08
The error seems pretty big for a decimal point error.

There is only one definition of [standard deviation]("http://en.wikipedia.org/wiki/Standard_deviation#A_simple_example"). Though there might be some approximation that works well for large sets. That's pretty much what I think is the situation here.

---

### Post by Whiffle on 2008-03-08
[quote=http://www.sbs.utexas.edu/jcabbott/courses/bio208web/labs/computer_lab.htm]
StdDev  An estimate of the standard deviation of a population, where the sample is all of the data to be summarized.
  StdDevp  The standard deviation of a population, where the population is all of the data to be summarized.
  Var  An estimate of the variance of a population, where the sample is all of the data to be summarized.
  Varp  The variance of a population, where the population is all of the data to be summarized.
[/quote]


Apparently it can be done in two different ways, although I'm having trouble figuring out what the differences are...

---

### Post by tgalati4 on 2008-03-10
The difference is 1/N versus 1/(N-1) as the divisor.  1/N gives you the true standard deviation, 1/(N-1) gives you the estimated standard deviation for a population using a sample of N.  As N gets large the two values converge as you would expect.

Using a small sample of a large population will give you a wider dispersion to better estimate that population's standard deviation.

---

### Post by Erdaron on 2008-03-10
> **tgalati4 said:**
> The difference is 1/N versus 1/(N-1) as the divisor.  1/N gives you the true standard deviation, 1/(N-1) gives you the estimated standard deviation for a population using a sample of N.  As N gets large the two values converge as you would expect.

Using a small sample of a large population will give you a wider dispersion to better estimate that population's standard deviation.

This seems like a pretty frivolous assumption to make without explicitly stating it. And what exactly is the point? The only reason to not use the exact formula is if the approximate formula requires fewer resources (which would make sense for a calculator).

It just seems to me that if ask the computer to calculate standard deviation of something, I expect it to calculate standard deviation of that thing, not what that something might be.

---


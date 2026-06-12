---
title: "Desktop Linux 10% market share"
date: 2009-11-05
forum: The Cafe
---

### Post by Pasdar on 2009-11-05
In a very long time from now. :D Since I'm a math wizz (and everything else actually) and I felt like doing this. I used six years of statistical information to come up with the following equation:

ULiNUX = 2.38*(YEAR-2000)^(0.26)

This equation can tell you how many desktop Linux users we will have in the year you enter. The answer is as accurate as the statistical data used, which is the statistical data of the World Wide Web Consortium.

Instead of "YEAR" type any year you wish, and it will give you the percentage of total world Linux desktop users in that year.


Edit: changed from linear to power function for better accuracy, see my later post.

---

### Post by PatrickBoyle on 2009-11-05
Sweet, in 2250 we'll have 120% market share!

I hope this is a joke.

---

### Post by tribaal on 2009-11-05
Funny :)

Since I'm a Python geek I decided to actually code it:
(for purists, I know I should be parsing command-line arguments and whatnot, but I'm lazy)

```


def linux_desktop_share(year):
    return (0.48 * ( year - 2000 ))

print linux_desktop_share(2021)

```

Oh gosh, I guess I'm really bored.
Have fun :)

- Trib'

---

### Post by Pasdar on 2009-11-05
This is definitely **NOT** a joke.

---

### Post by ZankerH on 2009-11-05
That's not how statistics works.

---

### Post by Pasdar on 2009-11-05
Oh and since the effect that Chrome OS, Android, MAMEO, etc will have on the market is not yet known... they can not be included. (in other words, unexpected effects other than those which have already happened can not be taken into consideration... e.g.: Canonical goes bankrupt, etc).

---

### Post by Pasdar on 2009-11-05
> **ZankerH said:**
> That's not how statistics works.

That's exactly how statistics works and is applied.

---

### Post by tuwe on 2009-11-05
so in the year 1996 linux had -1.92% market share?

---

### Post by Simian Man on 2009-11-05
No, that's not how statistics work.  For starters, growth and decay are best modeled using exponential functions - not linear ones.

---

### Post by Hallvor on 2009-11-05
> **Pasdar said:**
> In the year 2021... :) Since I'm a math wizz (and everything else actually) and I felt like doing this. I used six years of statistical information to come up with the following equation:

ULiNUX = (0.48*(YEAR-2000))

This equation with an error margin of less than 2.7%, will tell you how many desktop Linux users we will have in the year you enter. The answer is as accurate as the statistical data used, which is the statistical data of the World Wide Web Consortium.

Instead of "YEAR" type any year you wish, and it will give you the percentage of total world Linux desktop users in that year.


Wonderful. In 2208 all competition is wiped out. :lolflag:

---

### Post by hoppipolla on 2009-11-05
lol!

If I were to predict I would say more like within 2 years :)

---

### Post by saulgoode on 2009-11-05
> **Pasdar said:**
> The answer is as accurate as the statistical data used, which is the statistical data of the World Wide Web Consortium
To my knowledge, [WC3]("http://www.w3.org/Consortium/") provides no such statistical data. Could you provide a link?

---

### Post by NoaHall on 2009-11-05
Fail. 
This would only apply if media coverage and the knowledge of the common human remained at previous/current levels. However, as we all know media coverage has SHOT up. The knowledge of the common human is also rising. There are no stats that can be used for this.

---

### Post by Dr. C on 2009-11-05
> **Simian Man said:**
> No, that's not how statistics work.  For starters, growth and decay are best modeled using exponential functions - not linear ones.

A better model for the spread of FLOSS is a Logistic Function [http://en.wikipedia.org/wiki/Logistic_function]("http://en.wikipedia.org/wiki/Logistic_function")

At the early stages it can be approximated by an exponential function. The assumption that the rate of growth new GNU / Linux desktop users is proportional the the number of existing GNU / Linux desktop users is reasonable since GNU / Linux in the desktop is spread largely by word of mouth. The exponential model start to break down when one introduces Ubuntu to someone only to be told they are using Ubuntu or some other GNU / Linux distribution. It can also be approximated at the early stages as a linear function as the OP has done. 

One must keep in mind the limitation of these approximations. While using a linear approximation to predict 10% market share as the OP has done may be reasonably accurate the linear model will fail when trying to predict say 50% market share.

---

### Post by Merk42 on 2009-11-05
This is not how statistics work.
Take the other side of the coin, Microsoft. They went from 0% to their now ~90% market share, so therefore shouldn't their market share increase to 2021 as well?  Same for Apple.

Also, obligatory xkcd comic:
[img]http://imgs.xkcd.com/comics/extrapolating.png[/img]

---

### Post by PurposeOfReason on 2009-11-05
Yeah, I just woke up. . .

---

### Post by lukjad on 2009-11-05
In 1998 there was -0.96% for linux. Wow. We were NEGATIVE...

0.48 * (1 998 - 2 000) = -0.96

---

### Post by Aled Owen on 2009-11-05
What if another Kernel which was more controlled (in terms of, that is, less distros) and better than Linux came along and wiped out all thier market share?

---

### Post by Groucho Marxist on 2009-11-05
> **Pasdar said:**
> In the year 2021... :) Since I'm a math wizz (and everything else actually) and I felt like doing this. I used six years of statistical information to come up with the following equation:

ULiNUX = (0.48*(YEAR-2000))

This equation with an error margin of less than 2.7%, will tell you how many desktop Linux users we will have in the year you enter. The answer is as accurate as the statistical data used, which is the statistical data of the World Wide Web Consortium.

Instead of "YEAR" type any year you wish, and it will give you the percentage of total world Linux desktop users in that year.

Mark Twain once said, "Facts are stubborn, but statistics are more pliable." These are, at best, educated guesses based upon the supposition that marketplace trends will continue in a linear fashion. In other words, Linux will keep growing at a constant rate in terms of users.

---

### Post by Firestem4 on 2009-11-05
> **ZankerH said:**
> That's not how statistics works.

42% of all statistics are incorrect.

):P

---

### Post by Pasdar on 2009-11-05
> **Simian Man said:**
> No, that's not how statistics work.  For starters, growth and decay are best modeled using exponential functions - not linear ones.

You obviously are talking without knowledge of such things. You're not up against some average guy on this subject... just to let you know.

What kind of function is used depends on what fits the path best. In other words, one does not attempt to fit an exponential/power/logaritmic/etc function that does not 'fit' it well. So NO, you do NOT use an exponential function to show a growth or decay or whatever.... UNLESS it fits it best.

The following linear equation [I made the above equation even more accurate using a computer now]: **((YEAR-2000)/4)+2.31** (with YEAR >= 2003) has 94% correlation with the path. Only a stupid person would go with an exponential function: 2.38 *1.08^(YEAR-2000) (with YEAR >= 2003) which only has 89% correlation with the path.

However I did find that if I try to fit it in a power function: **2.38*(YEAR-2000)^(0.26)** I can stay as close as 96% to the path. So in this case i'd have to go with the power function. So my final equation on this matter is:

[SIZE="4"]2.38*(YEAR-2000)^(0.26)[/SIZE] ------- ((with YEAR >= 2003))

---

### Post by Pasdar on 2009-11-05
The following graph shows the growth rate from 2003 to 2030:

---

### Post by Simian Man on 2009-11-05
> **Pasdar said:**
> What kind of function is used depends on what fits the path best. In other words, one does not attempt to fit an exponential/power/logaritmic/etc function that does not 'fit' it well. So NO, you do NOT use an exponential function to show a growth or decay or whatever.... UNLESS it fits it best.
No **** sherlock.  My point is that the linear function you gave **could not possibly** be used to model Linux's growth accurately as it, and **any** linear function results in Linux having negative and over 100% marketshare at some point which is obviously ridiculous.

> **Pasdar said:**
> However I did find that if I try to fit it in a power function: **2.38*(YEAR-2000)^(0.26)** I can stay as close as 96% to the path. So in this case i'd have to go with the power function. So my final equation on this matter is:

[SIZE="4"]2.38*(YEAR-2000)^(0.26)[/SIZE] ------- ((with YEAR >= 2003))

OK that's better, but it isn't what you said to start with is it "math wiz"?

---

### Post by Tibuda on 2009-11-05
First, 6 is a very small number of observations to make such inferences. You need more to make use of the central limit theorem.

Second, when you are working with time series like this, just a regression of the variable on time (linear or not) is not the best aproach. Even if you got a big correlation, your inference won't be precise outside the time range of your data. ARIMA or other time series analysis techniques would be much more appropriate.

---

### Post by Pasdar on 2009-11-05
> **danielrmt said:**
> First, 6 is a very small number of observations to make such inferences. You need more to make use of the central limit theorem.

Second, when you are working with time series like this, just a regression of the variable on time (linear or not) is not the best aproach. Even if you got a big correlation, your inference won't be precise outside the time range of your data. ARIMA or other time series analysis techniques would be much more appropriate.

51 observations from 2003 to 2009 were used for this. However I wanted to make drawing the graph easier for myself so I took averages over each year.

---

### Post by Tibuda on 2009-11-05
> **Pasdar said:**
> 51 observations from 2003 to 2009 were used for this. However I wanted to make drawing the graph easier for myself so I took averages over each year.

Got it. Each observation is a month, or what?

If they are months, where's it in the equation or did you used the averages to estimate the equation?

---

### Post by JDShu on 2009-11-05
Missed the edit note and was staring at the power function wondering in what way it was linear LOL

I'd say the modified equation is pretty believable.

---

### Post by Tristam Green on 2009-11-05
> **Pasdar said:**
> You obviously are talking without knowledge of such things. You're not up against some average guy on this subject... just to let you know.

What kind of function is used depends on what fits the path best. In other words, one does not attempt to fit an exponential/power/logaritmic/etc function that does not 'fit' it well. So NO, you do NOT use an exponential function to show a growth or decay or whatever.... UNLESS it fits it best.

The following linear equation [I made the above equation even more accurate using a computer now]: **((YEAR-2000)/4)+2.31** (with YEAR >= 2003) has 94% correlation with the path. Only a stupid person would go with an exponential function: 2.38 *1.08^(YEAR-2000) (with YEAR >= 2003) which only has 89% correlation with the path.

However I did find that if I try to fit it in a power function: **2.38*(YEAR-2000)^(0.26)** I can stay as close as 96% to the path. So in this case i'd have to go with the power function. So my final equation on this matter is:

[SIZE="4"]2.38*(YEAR-2000)^(0.26)[/SIZE] ------- ((with YEAR >= 2003))

So you're saying that the equation *is* in fact hyperbolic, and not linear?

> **Pasdar said:**
> The following graph shows the growth rate from 2003 to 2030:

Yeah, that's what I thought you were saying.  It's a shame that others pointed it out before you came to the same conclusion :(

---

### Post by lukjad on 2009-11-05
okay everyone. I think it's time we all have a little lie down and remeber that we all love Linux/Ubuntu, we all love maths, and we don't really care if the graph shows what we would like to see instead of reality. ;)

---

### Post by orlox on 2009-11-05
> **Pasdar said:**
> 51 observations from 2003 to 2009 were used for this. However I wanted to make drawing the graph easier for myself so I took averages over each year.

Well then, fit them with a 50th order polynomial, or a fourier series with 51 terms. It will give you a perfect fit, with no error at all. However, probably one year after the data ends, the fit will just be crap and might go below 0% or over 100%.

A good statistical model doesn't just rely on finding a function that fits your data well. Unless there's some justification on the function you chose for the fit, the significance it has for later (or previous) times is null.

Could you share your data??

---

### Post by saulgoode on 2009-11-05
> **orlox said:**
> Could you share your data??
This. and a link to its source.

---

### Post by orlox on 2009-11-05
> **saulgoode said:**
> This. and a link to its source.

I looked around, and I think its [this]("http://www.w3schools.com/browsers/browsers_os.asp")

I attach a oocalc file with the data in a more useful format...

---

### Post by Tristam Green on 2009-11-05
Pasdar, my apologies for the quick pot-shot earlier.  I do not aim to decry any of your skills as a statistician, by any stretch.  You guys do things with .... numbers that I can never imagine :|

However, I hope this has been a great exercise in backing up one's data with sound numbers, when it comes to such things! :D

---

### Post by inobe on 2009-11-05
the topic doesn't make sense to me, maybe that's just me ?

[http://www.youtube.com/watch?v=rtp5gNhBZgo](http://www.youtube.com/watch?v=rtp5gNhBZgo)

i believe we should rethink even using the term "market share"

---

### Post by Giant Speck on 2009-11-05
You know, this thread is so fail, that I'm going to go install Windows.


TWICE.

---

### Post by orlox on 2009-11-05
I just approached this problem in a very simplistic model. Consider that the grouth rate of the market share X(t) is directly proportional to the current market share (due to mouth to mouth), and directly proportional to the share that doesn't use linux (the more people not using linux, the more people you can convince to use linux).

This drives to the following differential equation:

> dX/dt=A*X*(1-X)

(I'm using percentages as numbers from 0 to 1)

Here, A should be a positive number, so the growth rate is positive if 0<X<1

This equation has the benefit that solutions contained inside the range from 0 to 1 remain there (no such thing as that in 1950 it's predicted a negative market share). If I solve this equation, I get:

> X=(B*exp(-A*t)+1)^(-1)
(t in years)

Where B depends on the initial conditions. This thing is equivalent to:

> X=(B*exp(-A*(t-2003))+1)^(-1)

Where the offset given by including 2003 is used to avoid the program I use to fit to collapse from calculating very large exponentials.

If I fit this function to the data, I get the following values for A and B (approx):

> A=0.071, B=40.24

What does this gives me??
The attached plot, where the green line represents the fit, and the red dots the w3schools data.

---

### Post by Pasdar on 2009-11-05
danielrmt, I used averages... however I even made one with 35 independent observations... it gives practically the same result.

orlox, what I meant was not that one has to find an equation that fits the observations exactly. What I meant was that one has to find an equation that shows the general trend of things, and that that should be as close as possible to the observations. This doesn't mean that you deviate by giving the exact route.... that would be useless... and can obviously not be used to estimate how it would be the next month.

my model was to show where we are headed if things keep going the way they have done in the past years. It shows that if we care about market share, drastic changes are needed. But we'll have to see what effect Chrome OS will have. However its unlikely that "word of mouth" as is today and was in 2004 is any different now... ubuntu users have been propagating since day one... and that can already be seen in the stats.

I had calculated the growth rate, I just forgot what it was. It was very low... there are actually months where the growth rate was negative.. quite a few actually. and many months where there was no growth at all.

---

### Post by Zoot7 on 2009-11-05
Here's a blog on the linux market share:
[http://blog.linuxtoday.com/blog/2009/05/1-linux-market.html](http://blog.linuxtoday.com/blog/2009/05/1-linux-market.html)

I think 5-10% is a reasonable figure for it. It's not easy quantify mind you...

---

### Post by JDShu on 2009-11-05
> **inobe said:**
> the topic doesn't make sense to me, maybe that's just me ?

[http://www.youtube.com/watch?v=rtp5gNhBZgo](http://www.youtube.com/watch?v=rtp5gNhBZgo)

i believe we should rethink even using the term "market share"

considering the data being used, I guess we're defining Linux market share as: "percentage of internet users who can be identified as using linux"

With that definition, the debate can make sense.

---

### Post by AllRadioisDead on 2009-11-05
> **hoppipolla said:**
> lol!

If I were to predict I would say more like within 2 years :)
I'm not sure what's funnier, the responses to this thread or your prediction.

---

### Post by saulgoode on 2009-11-05
> **Pasdar said:**
> In a very long time from now. :D Since I'm a math wizz (and everything else actually) and I felt like doing this. I used six years of statistical information to come up with the following equation:

ULiNUX = 2.38*(YEAR-2000)^(0.26)

Your formula doesn't even fit the actual data:
```
Year   actual    computed   err
2003   2.34      3.17       35% 
2004   2.92      3.41       16%
2005   3.30      3.62       9%
2006   3.42      3.79       10% 
2007   3.42      3.95       15%
2008   3.78      4.09       8%
2009   4.10      4.21       2%

```

---

### Post by Pasdar on 2009-11-05
Its not supposed to fit it exactly. What it shows is the trend of usage (which would be close to that value).

---

### Post by Simian Man on 2009-11-05
On top of the questionable statistical analysis, there's the fact that the w3schools data is for *web developers* who browse their site.  Obviously web developers are going to be more likely to use Linux than the general population.  Come on, does anyone believe we have 4%??

---

### Post by Chronon on 2009-11-05
> **Pasdar said:**
> You obviously are talking without knowledge of such things. You're not up against some average guy on this subject... just to let you know.

What kind of function is used depends on what fits the path best. In other words, one does not attempt to fit an exponential/power/logaritmic/etc function that does not 'fit' it well. So NO, you do NOT use an exponential function to show a growth or decay or whatever.... UNLESS it fits it best.

The following linear equation [I made the above equation even more accurate using a computer now]: **((YEAR-2000)/4)+2.31** (with YEAR >= 2003) has 94% correlation with the path. Only a stupid person would go with an exponential function: 2.38 *1.08^(YEAR-2000) (with YEAR >= 2003) which only has 89% correlation with the path.

However I did find that if I try to fit it in a power function: **2.38*(YEAR-2000)^(0.26)** I can stay as close as 96% to the path. So in this case i'd have to go with the power function. So my final equation on this matter is:

[SIZE="4"]2.38*(YEAR-2000)^(0.26)[/SIZE] ------- ((with YEAR >= 2003))

1) You didn't specify a domain of validity and you didn't normalize your equation properly, that's why people are cracking wise about predictions of over-unity market share.

2) A linear function is a local approximation to an exponential function.  Over a short range of values (short defined by the scale factor of the exponential function) the linear function and a suitable exponential function will be almost indistinguishable.  For example, compare y=x with y=1-e^(-x) in the neighborhood of x=0.  Both increase linearly, initially (with the same slope and initial value).  However, the second function saturates at a value of 1 as x tends to infinity instead of growing without bound.  

Linear functions are fine as approximations, but you should always specify a domain of validity for approximate expressions.

---

### Post by BuffaloX on 2009-11-05
@ orlox
Your graph is the prettiest. :D


> **JDShu said:**
> considering the data being used, I guess we're defining Linux market share as: "percentage of internet users who **can** be identified as using linux"

With that definition, the debate can make sense.

Important observation IMO.

And if we are a little paranoid this could be added:
If you actually follow these statistics, there are often mysterious jumps, corrections and omissions.

The numbers only represent those that **are** identified based on (unknown) criteria.

---

### Post by hanzomon4 on 2009-11-05
> **lukjad007 said:**
> okay everyone. I think it's time we all have a little lie down and remeber that we all love Linux/Ubuntu, we all love maths, and we don't really care if the graph shows what we would like to see instead of reality. ;)

Not all of us love math

---

### Post by orlox on 2009-11-06
> **BuffaloX said:**
> @ orlox
Your graph is the prettiest. :D

Thanks :D

The function I get by solving that equation is called a [logistic function]("http://en.wikipedia.org/wiki/Logistic_equation"), and it's a pretty standard way to model growth rates that are proportional to the current population.

It's a very simple model, but it should reflect that mouth-to-mouth isn't an effective way to increase market share of linux in the short term. I think corporate support will make the market share increase significantly, but that's VERY hard to include in a model like this.

---

### Post by longtom on 2009-11-06
> **Pasdar said:**
> Since I'm a math wizz (and everything else actually) 

This is normally  as far as I should have read an moved on...

But the problem was interesting enough to read on.  Some of you came to interesting models and it was good to see, that the OP also moved away from a rather ridiculous linear model.

> 
The function I get by solving that equation is called a logistic function, and it's a pretty standard way to model growth rates that are proportional to the current population.

orlox, I like your way of thinking as well as your approach.  However, the fastest population growth takes place in places with the least IT coverage (and all the periphery that goes with it).
One would need to implement this in your model, which would need another prediction (that of development in 3rd and 4th world countries) in order to come to a conclusion.  Not impossible - but seeing the development in some (most?) African countries - some educated thumb sucking can turn into a hit and miss exercise faster than you can say "logic".

Just a thought from a non-whiz....:D

---


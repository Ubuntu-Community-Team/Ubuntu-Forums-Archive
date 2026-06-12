---
title: "Why do you run memtest for xxx number of hours/passes?"
date: 2012-07-13
forum: The Cafe
---

### Post by mikewhatever on 2012-07-13
Well, this is not, yet another, 'How many passes do I need' kind of thread. It is mostly about why, or how do you know that the certain number is right?
In other words, if you run 50 passes, why 50. Why not 20 or 100? 
Do you actually know why?

---

### Post by Cheesemill on 2012-07-13
Because if your RAM has bad blocks it won't necessarily show up every time that the specific address is accessed. You need to do at least a few passes to be sure that the errors are detected.

The more passes you do the more likely you are to detect any anomalies.

---

### Post by mikewhatever on 2012-07-13
> **Cheesemill said:**
> Because if your RAM has bad blocks it won't necessarily show up every time that the specific address is accessed. You need to do at least a few passes to be sure that the errors are detected.

The more passes you do the more likely you are to detect any anomalies.

That's rather obvious, but can you tell how many is 'a few', and if so, then tell also how you know that.

---

### Post by Cheesemill on 2012-07-13
No. I cant give you any numbers I'm afraid.

The systems that I have tested that I've suspected of having bad RAM have always failed within the first 10 passes. There's no way of knowing for sure though.

I just tend to start memtest running and check on it a day later.

---

### Post by Redblade20XX on 2012-07-13
> **mikewhatever said:**
> That's rather obvious, but can you tell how many is 'a few', and if so, then tell also how you know that.

I believe that we have to do a number of passes per hour because of the physical parameters of the memory.

 Memory, physically, is just an array of transistors that store the binary value they represent (memory address). Transistors are semi-conducting components that act somewhat like a switch therefore having the ability to represent binary one or zero. 

When a memory location goes bad, a representing transistor (or set of transistors) are going bad and due to the switching capabilities, can represent either the correct value of the memory space or an incorrect value at different time. This is the reason I believe it is necessary to test memory for a number of passes per hour.

Also transistors are effected by heat. The longer the system operates the higher the heat production will be and the greater the chance a going bad transistor will misbehave and represent an incorrect value thus giving a bad memory block.

Hopefully my assumptions are correct. :)

- Red

---

### Post by tgalati4 on 2012-07-14
30 passes.  Large sample size better predicts overall population.


[http://stattrek.com/sample-size/simple-random-sample.aspx](http://stattrek.com/sample-size/simple-random-sample.aspx)

---

### Post by mikewhatever on 2012-07-14
> **tgalati4 said:**
> 30 passes.  Large sample size better predicts overall population.


[http://stattrek.com/sample-size/simple-random-sample.aspx](http://stattrek.com/sample-size/simple-random-sample.aspx)

I guess the title is not clear enough. How do you know it's 30 passes and not 10 or 300?

---

### Post by Nixarter on 2012-07-14
> **mikewhatever said:**
> I guess the title is not clear enough. How do you know it's 30 passes and not 10 or 300?

The "Law of Large Numbers" :p

(basically what [tgalati4]("http://ubuntuforums.org/member.php?u=241895") said, but a little more detail)

You can calculate what sample size (in this case, number of passes) you need for a given accuracy.  If you want to be 95% sure, it is X passes, 99.99%, Y passes.  All you have to do is know the goal accuracy you want and just set up the problem (which is not always straight-forward).

Unfortunately, it is not completely accurate.  Everyone touched very accurately on the main points above, actually.  Heat alone has a huge effect. Even healthy RAM starts having faults at some point.  It is hard to take that into account to plug it into statistics formulas, though.  You have to know a lot about the RAM that you probably cannot find out, so you have to guesstimate.

Also, every stick of RAM will fail eventually, regardless of its state before initial testing.  On Large server farms they get gamma ray failures on a weekly or even daily basis.  So if you sample too many times, your RAM will fail :p  (but it would likely have to be many thousands of times lol).

---

### Post by mikewhatever on 2012-07-14
> **Nixarter said:**
> The "Law of Large Numbers" :p

(basically what [tgalati4]("http://ubuntuforums.org/member.php?u=241895") said, but a little more detail)

You can calculate what sample size (in this case, number of passes) you need for a given accuracy.  If you want to be 95% sure, it is X passes, 99.99%, Y passes.  All you have to do is know the goal accuracy you want and just set up the problem (which is not always straight-forward).

...

Can you show the calculation that arrives to the conclusion that, say, X passes gives 95% accuracy. ;)
In fact, any kind of calculation by anyone that plausibly links the number of memtest passes to RAM testing accuracy. I want something substantial, not abstractly remote theorisation.

---

### Post by Nixarter on 2012-07-14
> **mikewhatever said:**
> Can you show the calculation that arrives to the conclusion that, say, X passes gives 95% accuracy. ;)
In fact, any kind of calculation by anyone that plausibly links the number of memtest passes to RAM testing accuracy. I want something substantial, not abstractly remote theorisation.

nope!  It varies per stick of RAM, number of modules, and many other factors.  It would take too much time to calculate :p

I'm lucky enough that I haven't had symptoms similar to bad RAM sticks before.

Now, that obviously goes back to your first question.  Yes, there are reasons, but it isn't necessary to delve too far into it because it isn't mission-critical hardware or anything.  It seems more and more like you are asking whether or not people actually estimate probability first, or arbitrarily choose a number that should be "good enough."  It is a slightly different question, but I think it is far more likely for casual computer people.

---

### Post by fixitdude on 2012-07-14
I would be looking for cosmic rays passing through the RAM and trying to study how maybe bits it can flip as the RAM die sizes get smaller and smaller.

You might also run it during this weekend's solar storm and see if that does anything.

---

### Post by mikewhatever on 2012-07-15
> **Nixarter said:**
> nope!  It varies per stick of RAM, number of modules, and many other factors.  It would take too much time to calculate :p

I'm lucky enough that I haven't had symptoms similar to bad RAM sticks before.

Now, that obviously goes back to your first question.  Yes, there are reasons, but it isn't necessary to delve too far into it because it isn't mission-critical hardware or anything. 

No indeed. Naming one or two reasons would have been enough. Obviously, guessing doesn't apply, because it's just guessing (nothing wrong with that, as far as I am concerned). 
...and some hardware is actually very much mission critical.

> It seems more and more like you are asking whether or not people actually estimate probability first, or arbitrarily choose a number that should be "good enough."  It is a slightly different question, but I think it is far more likely for casual computer people.
Yes, I got curious why people advise to test for a certain number of passes/hours.

---

### Post by ssam on 2012-07-15
sometimes the problem is serious enough that it will fail on the first test. sometimes it is more erratic so it may only fail 1% of the time.

now if you want to know that your server is reliable enough to run for a year without a problem, then run memtest for a year. in practice you can't do that so you find a compromise. leaving it to run overnight is often a good compromise.

If you are worried about cosmics causing soft errors (flipping a bit, but doing no damage) then get ECC memory.

---

### Post by mikewhatever on 2012-07-15
> **ssam said:**
> sometimes the problem is serious enough that it will fail on the first test. sometimes it is more erratic so it may only fail 1% of the time.

now if you want to know that your server is reliable enough to run for a year without a problem, then run memtest for a year. in practice you can't do that so you find a compromise. leaving it to run overnight is often a good compromise.

If you are worried about cosmics causing soft errors (flipping a bit, but doing no damage) then get ECC memory.

Here we go again. Why is overnight a good compromise and not 4 or 24 hours, or, in fact, any other number of hours or passes?:P

---

### Post by Nixarter on 2012-07-15
Generally, most people seem to tend to run it until it has reached max operating temp to see if that induces an error.  For me, that is my general approach for testing stability in general (with overclocks and whatnot).  Sometimes I force fans down to make it run above normal temps, to make up for blockage from dust or whatever if I forget to clean it for a while.  Don't want graphical artifacts in my games, or miscalculations while looking for aliens.  :)

And I was assuming regular desktop users.  For mission-critical uses, standard RAM is not recommended. Hardened or specialized components (like ECC RAM already mentioned) would be used instead, and those are typically bespoke, and come with recommendations from the contracting company (they do all the calculations).

---

### Post by ssam on 2012-07-16
> **mikewhatever said:**
> Here we go again. Why is overnight a good compromise and not 4 or 24 hours, or, in fact, any other number of hours or passes?:P

overnight is better than 4 hours, more likely to catch a problem. 24 hours would be even better. but for me day time is useful time, that i dont want to spend sitting around waiting for memtest. night time is free time, where the computer can just be left on it own. so over night has the best effectiveness to 'my useful time' ratio.

same reason sleeper trains and night ferries are popular. it may take lots of wall clock time, but it takes very little useful time.

---

### Post by mikewhatever on 2012-07-16
> **ssam said:**
> overnight is better than 4 hours, more likely to catch a problem. 24 hours would be even better. but for me day time is useful time, that i dont want to spend sitting around waiting for memtest. night time is free time, where the computer can just be left on it own. so over night has the best effectiveness to 'my useful time' ratio.

That's at least a reason, but it has more to do with convenience rather then the effectiveness of RAM testing. Wouldn't you be spending some of your non-free time, had you known that running memtest overnight is next to useless? Alternatively, would you still be running memtest overnight, had you known that 2 hours is sufficient?

> same reason sleeper trains and night ferries are popular. it may take lots of wall clock time, but it takes very little useful time.
Sure, but usually, you know at least the approximate distance, or/and about how long you'll be travelling for, not so with RAM testing. It would be considered stupid to take a train that conveniently takes you to another state when you don't need to go there. You don't just buy a ticket for a convenient overnight train without knowing whether or not it travels far enough, and if not sure, you ask, or pick another train.
I wouldn't promote night trains for visiting a neighbour across the street, or night ferries for crossing the Atlantic Ocean.

---

### Post by ssam on 2012-07-17
> **mikewhatever said:**
> That's at least a reason, but it has more to do with convenience rather then the effectiveness of RAM testing. Wouldn't you be spending some of your non-free time, had you known that running memtest overnight is next to useless? Alternatively, would you still be running memtest overnight, had you known that 2 hours is sufficient?


I dont believe that any time is 'sufficient'. more time is better, but there are diminishing returns. So after 12 hours you might be 95% sure the RAM is fine, and after 24h your certainty might be 97%. (its hard to know what these numbers are, but i have a strong suspicion that as you increase the number of passes it will look like a cumulative distribution function of the normal distribution, [http://en.wikipedia.org/wiki/68-95-99.7_rule](http://en.wikipedia.org/wiki/68-95-99.7_rule)).

So you will never be 100% sure that the RAM is fine. There is no point in running it for a week to get to 99.99% because a weeks downtime might be worth more than just replacing the RAM. Also past 95% certainty that the RAM is fine you should be looking at other possibilities for the problems.

Actually if you do fine an error, then for that particular case you used a sufficient amount of time.

---

### Post by Grenage on 2012-07-17
I run about 4 hours worth of testing on any new build, and I've not encountered a situation where it looked clean, but later turned out to have problems.  Your mileage may vary; and undoubtedly does.

I used to know plenty of over-clockers who weren't happy until their system could run Prime for the best part of a week.  I used to run it for a few hours, and these days, such a routine isn't even likely to show a problem.

---

### Post by mikewhatever on 2012-07-18
> **Grenage said:**
> I run about 4 hours worth of testing on any new build, and I've not encountered a situation where it looked clean, but later turned out to have problems.  Your mileage may vary; and undoubtedly does.

I used to know plenty of over-clockers who weren't happy until their system could run Prime for the best part of a week.  I used to run it for a few hours, and these days, such a routine isn't even likely to show a problem.

...and how did you come up with the number?

---

### Post by Grenage on 2012-07-19
> **mikewhatever said:**
> ...and how did you come up with the number?

It was the length of the couple of films I watched with the other half.

---

### Post by mikewhatever on 2012-08-04
...anyone else wants to share insights?

---

### Post by chili555 on 2012-08-04
> **Cheesemill said:**
> Because if your RAM has bad blocks it won't necessarily show up every time that the specific address is accessed. You need to do at least a few passes to be sure that the errors are detected.

The more passes you do the more likely you are to detect any anomalies.Indeed. And for me, 'more' translates to the time it takes to sip a nice glass of red wine, have a nice eight-hour sleep, wake up, visit the restroom, brush my teeth, check out the market futures on CNBC, pour my coffee and then turn off memtest.

---

### Post by mikewhatever on 2012-08-05
So, what I learn from this very limited discussion is that RAM testing is kind of like religion, lots of opinions, zero knowledge or evidence. Isn't it surprising?

---

### Post by chili555 on 2012-08-05
>  zero knowledge or evidence. Well, not exactly zero:```
less /usr/share/doc/memtest86+/README.gz
```> 9) Execution Time
==================
The time required for a complete pass of Memtest86+ will vary greatly depending on CPU speed, memory speed and memory size. Memtest86+ executes indefinitely.  The pass counter increments each time that all of the selected tests have been run.  Generally a single pass is sufficient to catch all but the most obscure errors. However, for complete confidence when intermittent errors are suspected testing for a longer period is advised.Obviously, what exactly is 'longer' depends on many factors.

---


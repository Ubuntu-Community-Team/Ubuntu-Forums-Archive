---
title: "gambler's fallacy"
date: 2010-09-06
forum: The Cafe
---

### Post by chris200x9 on 2010-09-06
Can someone explain [this]("http://en.wikipedia.org/wiki/Gambler's_fallacy") to me, I get that if you flip a coin it has a 50-50 chance of heads or tails and it still has a 50-50 chance regardless of the past outcome, in theory. What I don't understand is how that works in practice, since it tends to 50-50 as n goes to infity how can the past not be relavent? I have looked at a sim of 5000 tosses and nowhere in it could I found more than about 10 or 12 in a row of any one side. I can bring up a problem let's say I have a raid-1 array with 2 drives, each has a 50% failure rate. Wouldn't I only have a 25% chance of failure? Likewise each coin toss each coin toss, or drive, has a 50% chance but overall the probability of getting a same coin, or failure, would decrease?

---

### Post by Frogs Hair on 2010-09-06
Can't find server.

---

### Post by TyrantWave on 2010-09-06
No. The drives have a 50% chance of failure.
Or, a 100/200 chance of failing - it's still a 50% chance there will be a failure. Not 25.

It's a 25% chance that they will *both* fail.


Likewise, it's always a 50% chance of being heads or tails.
The chance of getting two heads in a row is 25%.
3 heads in a row, 12.5%.

But still a 50% chance *each throw*


Gambler's fallacy assume that, say you have a 1% chance of something, after 99 tries you're more likely of having it happen. No, it still has a 1% chance.

---

### Post by spupy on 2010-09-06
> **chris200x9 said:**
> Can someone explain [this](http://en.wikipedia.orgwikiMonte_Carlo_Paradox) to me, I get that if you flip a coin it has a 50-50 chance of heads or tails _**and it still has a 50-50 chance regardless of the past outcome**_, in theory. What I don't understand is how that works in practice, since it tends to 50-50 as n goes to infity how can the past not be relavent? I have looked at a sim of 5000 tosses and nowhere in it could I found more than about 10 or 12 in a row of any one side. I can bring up a problem let's say I have a raid-1 array with 2 drives, each has a 50% failure rate. Wouldn't I only have a 25% chance of failure? Likewise each coin toss each coin toss, or drive, has a 50% chance but overall the probability of getting a same coin, or failure, would decrease?

Exactly. The outcome of one flip is not dependent on previous flips. The fallacy appears when the person in question will assume that a flip is in fact influenced by previous flips, and in such a way that the results will average 50-50.
5000 tosses will average to 50-50, but not because the single tosses are somehow influencing one another.

---

### Post by Strategist01 on 2010-09-06
The link was broken, are you talking about this article? [[Link]]("http://en.wikipedia.org/wiki/Gambler%27s_fallacy")

The results or probability of the outcome are always going to stay the same, as the result is not dependent upon the other results. Flipping a coin or rolling a dice are different to say taking a ball out of a bag and not replacing it - there the probability is determined by the outcome.

Computer sims don't do much for real, random results as computers don't have any real random numbers. The numbers they generate are part of a huge pattern which will eventually repeat itself. That's why if you have a look at the random part of the Java API it says that these functions will only generate pseudo random numbers.

Hope this answers your question?

---

### Post by Random_Dude on 2010-09-06
The probability of wining a coin toss is 50% every time you try it.
But the probability of wining 100 times ins a row is very slim.

The past is not relevant because each time you're tossing a coin, the coin doesn't "know" how many times it has flipped to one of the sides, so you'll get 50% chance every time.

I hope that I explained myself well.

Cheers :cool:

---

### Post by beew on 2010-09-06
> I get that if you flip a coin it has a 50-50 chance of heads or tails and it still has a 50-50 chance regardless of the past outcome, in theory. What I don't understand is how that works in practice, since it tends to 50-50 as n goes to infity how can the past not be relavent? I have looked at a sim of 5000 tosses and nowhere in it could I found more than about 10 or 12 in a row of any one side

The argument behind the gambler's fallacy_ assumes_ that you know_ a piori_ that it is a fair coin and that the tosses are independent. However, if you make a large number of tosses and almost always get heads then it would be more reasonable to think that those a pirori assumptions might have been wrong after all,--the game might be rigged. Still assumming tosses are independent (which is reasonable)you may want to update the priori assumption that the coin is fair based on your data. This is the idea behind Bayesian statistics. So yes, the gambler may not be wrong after all that he might have been cheated.

---

### Post by chris200x9 on 2010-09-06
> **TyrantWave said:**
> No. The drives have a 50% chance of failure.
Or, a 100/200 chance of failing - it's still a 50% chance there will be a failure. Not 25.

It's a 25% chance that they will *both* fail.


Likewise, it's always a 50% chance of being heads or tails.
The chance of getting two heads in a row is 25%.
3 heads in a row, 12.5%.

But still a 50% chance *each throw*


Gambler's fallacy assume that, say you have a 1% chance of something, after 99 tries you're more likely of having it happen. No, it still has a 1% chance.

exactly if 3 heads in a row would be 12.5% would not a tails be 87.5%

edit: wait am I looking at gambler's fallacy backwards? Does it essentially say "play a hot streak"?

---

### Post by voteforpedro36 on 2010-09-06
> **chris200x9 said:**
> exactly if 3 heads in a row would be 12.5% would not a tails be 87.5%

edit: wait am I looking at gambler's fallacy backwards? Does it essentially say "play a hot streak"?


The chance of flipping heads three times in a row is 12.5%. 
The chance of flipping heads each of those 3 individual times is still 50%.
The chance of flipping tails is 50% each time.
So, to your first statement, no.

---

### Post by chris200x9 on 2010-09-06
> **voteforpedro36 said:**
> The chance of flipping heads three times in a row is 12.5%. 
The chance of flipping heads each of those 3 individual times is still 50%.
The chance of flipping tails is 50% each time.
So, to your first statement, no.

right so wouldn't betting tails after 3 heads be good?

---

### Post by beew on 2010-09-06
> right so wouldn't betting tails after 3 heads be good?

Depends on your probability model. If you assume that the coin is fair and that the tosses are independent then it wouldn't make any difference. Regardless of what happened before, each toss has a 50-50 chance of showing a head or a tail.

However, if you take the Bayesian approach that the previous tosses actually inform you about the validity of the a piori assumption of fair coin, then you should bet on head because the data suggest that the coin is more likely to be loaded on one side, that is the revised probabilities for coming up with a head and a tail would no longer be 50-50 when taking previous observations into account, the revised probability for head is actually bigger if all three previous tosses showed up heads as a calculation using Bayes' theorem would show. Of course 3 is too small a number to give any meaningful statistical information, but you get the drift.

---

### Post by red_Marvin on 2010-09-06
You are just as likely to toss h-h-h as t-t-t or h-t-t it is the length of the sequence that counts.

---

### Post by Xkutzy on 2010-09-06
No. The coin does not know that it landed on heads the last three times. The chances that it will land on tails next time is still 50%.

The gamblers fallacy is that the past matters with independant random events. It does not. A single flip of a coin will always be a 50-50 chance. Even if it is part of a long sequence of flips.

---

### Post by chris200x9 on 2010-09-06
I don't know maybe I'm dense but as it approaches infinity it tends to 50-50, so how can you say that 20 heads has no effect on the tails. It's like saying ((infinity + 20) / 2) is equal to ((infinity) / 2). Statisticaly it should go to ((infinity) / 2) and ((infinity) / 2) to make it 1:1, so to realize that 1:1 wouldn't the heads need to decrease by 20 as n goes to infinity, thus giving tails the ever so slight statistical advantage?

---

### Post by red_Marvin on 2010-09-06
It does not work that way since you cannot do that kind of math with infinity.

---

### Post by chris200x9 on 2010-09-06
> **red_Marvin said:**
> It does not work that way since you cannot do that kind of math with infinity.

What math, saying something that should approach 50-50 should approach 50-50?

---

### Post by standingwave on 2010-09-06
Why, infinity is exactly as long as it takes for the coin flips to balance out at fifty-fifty... :p

Dice, cards, roulette wheel have no memory, provided that they're honest.

---

### Post by treesurf on 2010-09-06
This issue is humorously addressed in the opening scene of the film Rosencrantz and Guildenstern are Dead. A great film, by the way:

[http://www.youtube.com/watch?v=T4SVVKuOr0c](http://www.youtube.com/watch?v=T4SVVKuOr0c)

---

### Post by chris200x9 on 2010-09-06
> **standingwave said:**
> Why, infinity is exactly as long as it takes for the coin flips to balance out at fifty-fifty... :p

Dice, cards, roulette wheel have no memory, provided that they're honest.

Ok, you say infity is how long it takes to even out...so heads must decrease by 20 or tails increase by 20 to even it out, either way tails has an advantage.

---

### Post by standingwave on 2010-09-06
> **chris200x9 said:**
> Ok, you say infity is how long it takes to even out...so heads must decrease by 20 or tails increase by 20 to even it out, either way tails has an advantage.It was just a joke. There is no evening-out involved. Say heads  comes up ten times in a row. The odds of tails coming up on the next flip is still 1:1.

Infinity isn't a number as we usually think of numbers. It's more of a direction, really. It's as big as we need it to be which means that's it's useless to apply it to predicting the actions of some invisible hand balancing out (truly) independent and (truly) random processes.

---

### Post by chris200x9 on 2010-09-06
> **standingwave said:**
> It was just a joke. There is no evening-out involved. Say heads  comes up ten times in a row. The odds of tails coming up on the next flip is still 1:1.

Infinity isn't a number as we usually think of numbers. It's more of a direction, really. It's as big as we need it to be which means that's it's useless to apply it to predicting the actions of some invisible hand balancing out (truly) independent and (truly) random processes.

lim n -> infity of tossing a coin approaches 50-50, but you can not say the bigger number evens out with the smaller number? Not to harp on this but it seems like a giant contradiction, head's frequency does not decrease and tail's does not increase...but we still get 50-50 when in the begining tails started with a huge (not huge in this case, but could be in other examples) deficite?!

---

### Post by TyrantWave on 2010-09-06
Here's where you're wrong though:

*Lim n -> Infinity, P approaches 50:50.*


No, P is ALWAYS 50:50, it doesn't approach anything.

If you get HTTHTHTHH, it's the exact same chance that you'd get THHTHTHTH.
If you get HHHHHHH, it's the same chance as getting HHHHHHT.
If you get HHTTHHTT, it's the same chance as getting HHHHTTTT.

Tails never started with a huge deficit.

---

### Post by standingwave on 2010-09-06
> **chris200x9 said:**
> lim n -> infity of tossing a coin approaches 50-50, but you can not say the bigger number evens out with the smaller number? Not to harp on this but it seems like a giant contradiction, head's frequency does not decrease and tail's does not increase...but we still get 50-50 when in the begining tails started with a huge (not huge in this case, but could be in other examples) deficite?!No. You can't. Because infinity is as big as it needs to be. I play a lot of poker and while rushes (a string of good cards) happens, I don't believe in rushes, .i.e. that a player on a rush will continue to get good cards. This is the [Fallacy of the Hot Hand]("http://www.fallacyfiles.org/hothandf.html"), which you will note makes a prediction that is exactly the opposite of the one made by the Gambler's Fallacy.

---

### Post by chris200x9 on 2010-09-06
> **TyrantWave said:**
> Here's where you're wrong though:

*Lim n -> Infinity, P approaches 50:50.*


No, P is ALWAYS 50:50, it doesn't approach anything.

If you get HTTHTHTHH, it's the exact same chance that you'd get THHTHTHTH.
If you get HHHHHHH, it's the same chance as getting HHHHHHT.
If you get HHTTHHTT, it's the same chance as getting HHHHTTTT.

Tails never started with a huge deficit.


I still don't get it, i guess I'm dumb. Requesting close...

---

### Post by YuiDaoren on 2010-09-06
See, this is why I call lotteries "a tax upon those unfamiliar with probability theory".

---

### Post by red_Marvin on 2010-09-06
> **chris200x9 said:**
> What math, saying something that should approach 50-50 should approach 50-50?

I'm just saying that you cannot treat infinity as a regular number
and put it into equations like infinity+2 etc. Such equations lack
mathematical meaning.

It will approach 50/50, not because twenty heads will be compensated by twenty tails somewhere in the future, but because
*any* _finite_ sequence is bound to have neglible influence on the whole since the whole sequence is infinite.

Toss a coin with a 0.5 probability for tails *n* times, of which *m* tosses seem to have another probability for tails, say 1:
Calculate the mean probability as an average of the tosses:

*p_avg = (0.5(n-m)+1m)/n*

As you will see, as long as *m* is a finite number (eg 20) the average will still go towards .5 as *n* grows.

The concept of infinity is as such, that you can not use it as a number directly, but still sometimes figure out properties
of problems using the concept of infinity by looking at how the problem behaves at larger and larger numbers.

---

### Post by itismesteve on 2010-09-06
Hey guys i think he is trolling,

```
Series Size , Continue , Change , Percentage Difference
          1 ,    24916 ,  24997 ,    0 
          2 ,    12566 ,  12350 ,   -1 
          3 ,     6294 ,   6271 ,    0 
          4 ,     3110 ,   3184 ,    2 
          5 ,     1586 ,   1524 ,   -4 
          6 ,      794 ,    792 ,    0 
          7 ,      401 ,    393 ,   -2 
          8 ,      210 ,    191 ,   -9 
          9 ,      103 ,    107 ,    3 
         10 ,       57 ,     46 ,  -23 
         11 ,       28 ,     29 ,    3 
         12 ,       11 ,     17 ,   35 
         13 ,        5 ,      6 ,   16 
         14 ,        3 ,      2 ,  -50 
         15 ,        2 ,      1 , -100 
         16 ,        1 ,      1 ,    0 
         17 ,        0 ,      1 ,  100
```

---

### Post by spupy on 2010-09-06
> **YuiDaoren said:**
> See, this is why I call lotteries "a tax upon those unfamiliar with probability theory".

This reminds me of a hilarious "special" offer on some TV game long ago. Basically, you call them on the phone and get a ticket. Then if they pick your ticket (it's random), you get to play the game on TV next week.
The special offer said:
"This week you get TWO tickets per phone call instead of one!"

I lol'd.

---

### Post by YuiDaoren on 2010-09-06
> **spupy said:**
> This reminds me of a hilarious "special" offer on some TV game long ago. Basically, you call them on the phone and get a ticket. Then if they pick your ticket (it's random), you get to play the game on TV next week.
The special offer said:
"This week you get TWO tickets per phone call instead of one!"

I lol'd.
Hahahaha! #-o:D

Jeeeez this stuff can make one's sides ache.

---

### Post by Shippou on 2010-09-06
I believe the OP just wants to confirm what is the probability that after n tosses, I get n heads (think of it as a question asked in a different context).

Let's say that I toss n coins. What is the probability that I get m heads?

This is solved by applying the Binomial distribution:

nCx(p^x)(p^(n-x)),

where n is the sample space (no. of total tosses), p the probability of each toss, x the number required (in this case, the number of heads).

In terms of probability concerning a single coin toss, the other posters are right: the probability of getting a head in a single toss is as equally likely as getting a tail: 50%, or 0.5, or 1/2. The event is independent, as a single coin toss DOES NOT depend on previous tosses (assuming a fair coin: i.e. not a two-sided coin or a modified coin).

I do hope this clears the issue a little bit.

---


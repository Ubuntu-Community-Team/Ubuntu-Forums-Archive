---
title: "[OffTopic] Probability"
date: 2005-12-09
forum: The Cafe
---

### Post by bytter on 2005-12-09
Heya there ppl,

This is WAYYY of topic... I'm searching a forum to answer me some doubts I have about statistics and probabilities. I'll have an examination next tuesday and I can't seem to work out this exercise:

"Suppose you do target practice. You fire a weapon several times and write down the number of times you got a certain score. Suppose that, in the end, you figure the following probability function:

Score:       2      4      6     8     10
Probability: 25% 30% 30% 10%  5%

In other words, you have a 25% probability of hitting the outer ring of the target (and get a score of 2), 5% of hiting the most inner ring (and get a score of 10), etc...

The question is... Suppose you fire 10 times. What is the probability of hiting the center ring in more that one shot? And if you fire fire 60 times, what is the probability of making a comulative score of 300? And what about the probability of the comulative score of 26 been achieved in the first three shots?"

I really apreciate if someone could a) explain me this (a simple answer is no good.. I must understand this :D), b) point out to a forum about statistics and/or c) recommend a good, practical book, not filled with demonstrations and theory but direct, simple explanations...

A very huge THANKS in advance!

---

### Post by hesee on 2005-12-09
[QUOTE=bytter]What is the probability of hiting the center ring in more that one shot?[/QUOTE]

This one I could maybe handle:
Probability to hit more than once P(x>1) is the same as inverse probability if hitting zero or one time to the center ring, 1 - [P(x=0) + P(x=1)].

P(x=0) = (0.25+0.30+0.30+0.10)^10 = 0.5987
P(x=1) = [(probability you hit 9x outside center) x (probability you hit 1x inside center ring)]x10 = (0.25+0.30+0.30+0.10)^9 x (0.05) x 10 = 0.3151

therefore, P(x>1) = 1 - (0.5987+0.3151) = 0.0862

I might be wrong, it's couple of years since I studied a statistics course, so please correct if this is wrong :)

---

### Post by bytter on 2005-12-09
Heya there,

Thanks for your reply...

[QUOTE=hesee]P(x=1) = [(probability you hit 9x outside center) x (probability you hit 1x inside center ring)]x10 = (0.25+0.30+0.30+0.10)^9 x (0.05) x 10 = 0.3151[/QUOTE]

Interesting solution (dunno if the result is correct, since I don't have the answers). But why do you multiply by 10?

---

### Post by Stormy Eyes on 2005-12-09
Doesn't the probability depend in part on the gunner's skill with the rifle?

---

### Post by hesee on 2005-12-09
[QUOTE=bytter]Interesting solution (dunno if the result is correct, since I don't have the answers). But why do you multiply by 10?[/QUOTE]

Because answer looks better :) No, really, I thought that without multiplication, it's just probability, that first 9 hits outside center and last one hits inside center. So, to take every possibility (first hits in the center, second, etc...) into account, I have to multiply with total number of possibilities. This is the part which i'm not 100 percent sure, though.

---

### Post by bytter on 2005-12-09
[QUOTE=Stormy Eyes]Doesn't the probability depend in part on the gunner's skill with the rifle?[/QUOTE]

Yes.. That's why the gunner's did a first-run and calculated his own probability, given by the function above...

---

### Post by hesee on 2005-12-09
[QUOTE=Stormy Eyes]Doesn't the probability depend in part on the gunner's skill with the rifle?[/QUOTE]

Hmm, yeah... But these are probabilities for gunner X. For me those would be [0.08, 0.02, 0.00, 0.00, 0.00], rest 90% out of the target :???:

---

### Post by bytter on 2005-12-09
[QUOTE=hesee]Because answer looks better :) No, really, I thought that without multiplication, it's just probability, that first 9 hits outside center and last one hits inside center. So, to take every possibility (first hits in the center, second, etc...) into account, I have to multiply with total number of possibilities. This is the part which i'm not 100 percent sure, though.[/QUOTE]

Ok.. That's strange...
But here's one that I know.. Given a dice, the probability of having a 6 at the second, third and fourth throw is:

P(X = 1) = (5/6) * (1/6)
P(X = 2) = (5/6) * (5/6) * (1/6)
P(X = 3) = (5/6) * (5/6) * (5/6) * (1/6)
P(X = n) = (5/6)^k * (1/6)

So I would say that your reasoning is very similar to this one... Still, can't get the x10 part...

---

### Post by hesee on 2005-12-09
[QUOTE=bytter]Ok.. That's strange...
But here's one that I know.. Given a dice, the probability of having a 6 at the second, third and fourth throw is:

P(X = 1) = (5/6) * (1/6)
P(X = 2) = (5/6) * (5/6) * (1/6)
P(X = 3) = (5/6) * (5/6) * (5/6) * (1/6)
P(X = n) = (5/6)^k * (1/6)

So I would say that your reasoning is very similar to this one... Still, can't get the x10 part...[/QUOTE]

Ok, here's the probab. that we get 6 in third throw:
P(X = 2) = (5/6) * (5/6) * (1/6)

What's the probab. that we get 6 only once, but no matter if it's first, second or third throw? Must be higher than probab. above?

I would guess it's:
3 x P(X = 2) = 3 x (5/6) * (5/6) * (1/6)

---

### Post by bytter on 2005-12-09
[QUOTE=hesee]What's the probab. that we get 6 only once, but no matter if it's first, second or third throw? Must be higher than probab. above?[/QUOTE]

That must be the inverse probability of NOT getting a 6 with 3 throws. Which is:

P(X > 1) = 1 - P(X = 0) = (5/6)^3

Right?

---

### Post by hesee on 2005-12-09
[QUOTE=bytter]That must be the inverse probability of NOT getting a 6 with 3 throws. Which is:

P(X > 1) = 1 - P(X = 0) = (5/6)^3

Right?[/QUOTE]

Actually not, that is the "probability that we get 1 or more 6s, and not matter if its first,second or third".
That's different than:
"probab. that we get 6 only once, but no matter if it's first, second or third throw".

---


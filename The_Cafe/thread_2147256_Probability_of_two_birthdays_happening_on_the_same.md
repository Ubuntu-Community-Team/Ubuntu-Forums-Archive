---
title: "Probability of two birthdays happening on the same day"
date: 2013-05-21
forum: The Cafe
---

### Post by AmbiguousOutlier on 2013-05-21
It was two peoples birthdays yesterday in my team at work of 20 people. We started to have a debate on what the probability of that happening. Mathematically, you'd work out 1 minus the probability of it not happening. ie;

1 - (364/365) * (363/365) ... (346/365) = 0.41


However logically, the odds of 2 people (A and B) having the same birthday is 1/365. If you introduce a third person (C) then A being as same B =1/365, A same C = 1/365 and B same C = 1/365 or 3/365. If you introduce a fourth person you have 6 combinations therefore the odds are 6/365. The combinations for 20 people are 190 but 190/365 is 0.52?

Obviously this method is flawed as a team of 28 people have 378 combinations which would give a probability greater than 1!

Why is the second method wrong, what am I missing?

---

### Post by Luffield on 2013-05-21
I think your mistake is ignoring the situations of A=B=C and its likes.

---

### Post by AmbiguousOutlier on 2013-05-21
> **Luffield said:**
> I think your mistake is ignoring the situations of A=B=C and its likes.

But if I'm ignoring certain multiple combinations then should surely make my odds longer not shorter, therefore if I introduce that extra level of complexity it would increase the probability of it happening?

---

### Post by sanderj on 2013-05-21
Instead of 'birhtday' take 'sex' (meaning: male or female), and check out where your reasoning goes wrong ...

---

### Post by eriktheblu on 2013-05-21
My sample population contains nearly 200,000. Birthdays cover the entirety of the calendar. The most common date had a ration of 1 in 312, where the least common (excluding Feb 29) was 1 in 438. Feb 29 rated 1 in 1660.

In that same sample, yesterday's birthday rate was 1 in ~396.

My fractional math is a bit rusty, but I think that means the chance of a random set of 2 people having a birthday yesterday would be something like 1 in 156816. In a group of 28, the probability that 2 would share the date increases to what I figure (probably incorrectly) to 1 in 5600.

---

### Post by PJs Ronin on 2013-05-21
The  event of at least two of the *n* persons having the same birthday is complementary to all *n* birthdays being different. Therefore, its probability *p*(*n*) is
[IMG]http://upload.wikimedia.org/math/4/7/b/47b2161d496e2cc19bd74947266127cd.png[/IMG][URL="http://en.wikipedia.org/wiki/Birthday_problem"]
http://en.wikipedia.org/wiki/Birthday_problem[/URL]

You only need n >= 23 to get a >50% probability 2 people share the same birthday.

---

### Post by tgalati4 on 2013-05-21
It's an easy way to earn some money if you are teaching a class with ~30 people.  Put $10 up for grabs and have folks in the class match it.  Then go around and announce the birthdays.  You could end up with some money.  If you lose, you are only out $10.

---

### Post by Copper Bezel on 2013-05-21
PJs Ronin - That's where the OP started, though. = )

> **RhysGM said:**
> But if I'm ignoring certain multiple combinations then should surely make my odds longer not shorter, therefore if I introduce that extra level of complexity it would increase the probability of it happening?

sanderj's answer really covers this nicely, but to explain the logic:

Using your second method actually just double-counts cases where more than two people have the same birthday. You're right that for any two people, the chance would be 1/365. That's where the proper method starts, too, after all. But think about what you're testing. In the group of three, the first test is for A and B to be the same, which is a 1/365 chance, and the second test is for B and C to be the same, also a 1/365 chance, and the third for A and C, the same. If A, B, and C are all the same (a 1/365^2 chance,) that meets the conditions for both tests, so if you simply add the probabilities, it gets counted three times, once for each case - but it's still just *one* case where two people share a birthday (and incidentally a case where three people do, but the original question being answered doesn't care about that.) If you take 3/365 and subtract out 2/365^2, you get the proper probability.

I guess that for a group of five, you'd need to remove four cases where three but not four or five people shared a birthday, four cases where four but not five people shared a birthday, and four cases where five shared a birthday. So for a group of 28....

---

### Post by monkeybrain2012 on 2013-05-22
> **RhysGM said:**
> 
However logically, the odds of 2 people (A and B) having the same  birthday is 1/365. If you introduce a third person (C) then A being as  same B =1/365, A same C = 1/365 and B same C = 1/365 or 3/365. If you  introduce a fourth person you have 6 combinations therefore the odds are  6/365. The combinations for 20 people are 190 but 190/365 is 0.52?

Obviously this method is flawed as a team of 28 people have 378 combinations which would give a probability greater than 1!

Why is the second method wrong, what am I missing?

Your claim is P(A=B) + P(B=C) + P(A=C) = P(A=B or B=C or A=C)  but this  is wrong because the events  A=B, A=C and B=C are not mutually exclusive  so their probabilities don't add.

If you use the correct formula (the inclusion-exclusion principle) for  A, B, C then with some algebra you will see it works out to the same  answer as with the first method.

(the inclusion-exclusion principle, for events E1, E2, E3, P(E1 or E2 or  E3) = P(E1) + P(E2) + P(E3) - P(E1 and E2) - P(E2 and E3) - P(E1 and  E3) + P(E1 and E2 and E3) . It can generalize to more events. If the  events E's are mutually exclusive, all the probabilities involving "and"  are 0 and  hence the probabilities of mutually exclusive events add.)

Edited: Just saw Copper Bezel's post, he explained the inclusion-exclusion very well without equations.

---

### Post by rewyllys on 2013-05-22
The problem being discussed in this thread has been widely known as the "Birthday Problem" since being made famous by William Feller in his classic treatise on probability, *An Introduction to Probability Theory and Its Applications*, first published by Wiley & Sons in 1950.  (BTW, I had to buy a copy of the first edition for a course I took in the 1950s, and I still have it.)

 A nice presentation of the solution is on the Web at this Michigan State University [Webpage]("http://archive.lib.msu.edu/crcmath/math/math/b/b248.htm").

---

### Post by 3Miro on 2013-05-23
Nevermind

---

### Post by cprofitt on 2013-05-23
Hmm... interesting thread... I was once in a group of 90 people and had a person who was born on the same day and year as me... several people have shared my birthday, but that was the only one that was same year and day.

---

### Post by vladster on 2013-05-25
My wife and her brother are born both on 30th april with 2 years difference

---

### Post by rewyllys on 2013-05-28
Since writing my previous post (#10) in this thread, I've happened across a couple of interesting sidelights on the Birthday Problem.

They struck me as worth writing up, and I've done so on this [Webpage]("https://www.ischool.utexas.edu/~wyllys/IRLISMaterials/MathematicalExpertiseVsComputation02.html").

---


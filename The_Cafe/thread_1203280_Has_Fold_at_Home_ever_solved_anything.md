---
title: "Has Fold at Home ever solved anything?"
date: 2009-07-03
forum: The Cafe
---

### Post by Lateforgym on 2009-07-03
This is a serious question, not an attempt to discourage it. I tried to look some of this up but couldnt find answers:

I'm just wondering, I have seen various computer forums supporting it over the years, but I never read anything outside of that about some breakthrough made possible by allowing someone to cluster computers. 

In fact I have never heard anything about any success of significance with it, that couldnt be done in a typical college LAN.  I mean why not tell Standford co-eds just to leave all computers on? If all the thousands Stanford Co-eds left every computer on, as a mandatory part of their enrollment, and the science classes ran their folds from 1 till 6 AM, wouldnt that be plenty of computing power?

I also wonder if Folding is actually just a waste of electricity. Being that folding relates to a science class they probably arent running folds 365 days a year, so I wonder how many people run the fold program, around the country, leaving their computers on all the time, but maybe its only used a couple weeks out of the year?

---

### Post by t0p on 2009-07-03
> **Lateforgym said:**
> This is a serious question, not an attempt to discourage it. I tried to look some of this up but couldnt find answers:


[This]("http://straddle3.net/context/02/021023.en.html") is the 7th link on the results page for Google query: **fold at home success**.  So I really do wonder how you "tried to look some of this up but couldn't find answers."  But it is true that this protein thing is about the only success anyone mentions.

> **Lateforgym said:**
> 
I also wonder if Folding is actually just a waste of electricity. Being that folding relates to a science class they probably arent running folds 365 days a year, so I wonder how many people run the fold program, around the country, leaving their computers on all the time


Search this forum for "uptime" (actually, use Google with modifier site:ubuntuforums.org - this site's search function is crap) and you will quickly discover that lots of people leave their machines on 24/7.  Extrapolate the numbers: at any given moment there are billions of computers switched on but doing jack.  Folding@home can prevent the resources they're using up from being wasted.

---

### Post by xir_ on 2009-07-03
even if it 'solves' anything the method it uses is a very poor model and may not be real world reflective anyway.

In reality even hydrogen gas cannot be modeled (because it has more than one electron), yet alone proteins.

So id take a pinch of salt

---

### Post by Pogeymanz on 2009-07-03
> **xir_ said:**
> even if it 'solves' anything the method it uses is a very poor model and may not be real world reflective anyway.

In reality even hydrogen gas cannot be modeled (because it has more than one electron), yet alone proteins.

So id take a pinch of salt

What do you mean it's a poor model? Sure, hydrogen gas can't be exactly solved, but numerically, we can solve a lot of complicated systems with high precision.

Until we develop some new math, that's going to have to be good enough.

---

### Post by xir_ on 2009-08-05
> **Pogeymanz said:**
> What do you mean it's a poor model? Sure, hydrogen gas can't be exactly solved, but numerically, we can solve a lot of complicated systems with high precision.

Until we develop some new math, that's going to have to be good enough.


Depends what you term high precision, if the exchange between electrons isn't correctly modelled then the resulting electrostatics inside the molecule may give and incorrectly folded active site and suggest bad drug candidates. 

beyond that i doubt that folding at home is solving the molecular Hamiltonian, it most likely is using a empirical forcefield such as the amber forcefield. This is very approximate and most chemists find its accuracy to be very lacking, i even worked for a professor who explicitly used such a forcefield as an example of a bad approximation these methods can be in his research.

A molecule the size of a tertiary protein would normally take months to model, not to mention have its structure optimised with the something like density functional theory and then still the result would not be 'true' as often the molecules are not modelled in their natural solvent environment.

I do agree with you that new math is needed (hence my interest in the field), but additional to that its the computing power thats holding us back (hence the months to make calculations). Unfortunately the accurate (electronic structure) methods do not lend well to distributed computing systems as they will have massive matrix elements to solve and splitting these would cause nightmares. 

To top if off one of the main and most accurate software packages for solving the Hamiltonian doesn't scale linearly after 2 processors and then doesn't scale at all beyond 8, not that the coding is bad, but that most of it is written in Fortran77 without parallel processing in mind.

---

### Post by JDShu on 2009-08-05
[http://folding.stanford.edu/English/Papers](http://folding.stanford.edu/English/Papers)

Some of the links need subscriptions to read the full article.

---

### Post by xir_ on 2009-08-06
> **JDShu said:**
> [http://folding.stanford.edu/English/Papers](http://folding.stanford.edu/English/Papers)

Some of the links need subscriptions to read the full article.


thanks for the brilliant link i shall read some of these with great interest.

I am impressed that folding is using any form of molecular dynamics, unfortunatly that is still a very weak method for constructing molecular properties. a step above forcefield optimizations, but not by much.

---

### Post by Johnsie on 2009-08-06
nano nano! Oh wait, this is not the alien one.

---


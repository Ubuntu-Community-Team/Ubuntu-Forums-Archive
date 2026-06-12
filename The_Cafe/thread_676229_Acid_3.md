---
title: "Acid 3"
date: 2008-01-23
forum: The Cafe
---

### Post by Xbehave on 2008-01-23
how well do browsers perform on acid 3?
weirdly atm for me acid 3 performs best on FF3 better than konq 3/4, but then again i dont have opera
for me FF3 gave me 58/100 had a few random artifacts and was in greyscale
where as konqueror didn't even start it got a score of 1

I know its running the race not winning that matters but it would be nice to know how well browsers perform before actively trying to improve standard compliance

* i realize as of posting this acid 3 is unfinished but its only missing 6 tests so 58 vs 1 is quite a significant comparison

---

### Post by Darkhack on 2008-01-23
Even though it may be missing only six tests, the ones that aren't missing are still extremely buggy.  Konqueror has great standards support and I'd be my life on the fact that it's a bug in the test that caused such a low score.

Opera got a 51 for me.  Also, what version of Konqueror were you using, 3 or 4?

---

### Post by Polygon on 2008-01-23
the acid test is a horrible way to test browser compatibility.

funny thing, firefox fails the acid test, but it renders every page ive seen in a while correctly.

Just another useless feature the firefox developers have to spend time working on rather then other more important things

> 
Because Acid2 tests how web browsers deal with faulty code, the test is intentionally not written to W3C CSS standard specifications, and fails validation


im not sure if acid3 is the same way, but this in no way promotes 'standards' or not, it just means your browser deals with bad code made by amateur or whatever web designers/coders.

---

### Post by Xbehave on 2008-01-24
> **Darkhack said:**
> Opera got a 51 for me.  Also, what version of Konqueror were you using, 3 or 4?
4 as 3 crashes. yeah iots proabably buggy code konqueror almost passed acid 2 first.

i thought ACID 1/2/3 were written to standards, where did you get that quote?
acording to the acid site:
> Acid2 is a complex web page. It uses features that are not in common use yet, because of lack of support, and it crams many tests into one page.
the way i understand it the acid tests simply show if a browser is standards compliant, by using stuff that isn't normally used, to prevent a cycle of failure

feature isn't render well so rarely used
features are rarely used so rendering isn't improved
...
etc

end result is that browsers render standards well and web devs can code to existing standards instead of whatever works!

---

### Post by ~LoKe on 2008-01-24
The acid3 test isn't even finished...

---

### Post by Polygon on 2008-01-24
that quote is from wikipedia. It does say its meant to 'test' standards, but its also designed to break browsers.

---

### Post by p_quarles on 2008-01-24
> **Polygon said:**
> that quote is from wikipedia. It does say its meant to 'test' standards, but its also designed to break browsers.
It says the same thing on the Acid2 test site, but makes it slightly more clear that CSS is the *only* invalid part of the test. Everything else is written to W3C standards.

---


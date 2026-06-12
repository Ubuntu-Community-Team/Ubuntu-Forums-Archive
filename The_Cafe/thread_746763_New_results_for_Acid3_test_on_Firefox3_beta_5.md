---
title: "New results for Acid3 test on Firefox3 beta 5"
date: 2008-04-05
forum: The Cafe
---

### Post by PmDematagoda on 2008-04-05
I have just checked out the acid3 test with Firefox3 beta 5 and the result has now risen to 70/100, this is really great since Firefox3 is still in beta and has a bit of a long way to go before being released yet they have managed to achieve 70/100 on the acid3 test.

I have a feeling that this means the release of Firefox3 is going to be a big one, nice job Mozilla keep up the good work:lolflag:.

---

### Post by tamoneya on 2008-04-05
is it just me or has it taken a lot less time for browsers to start passing the acid3 than the acid 2.  I feel like the acid3 wasnt made hard enough and we are already needing acid4.

---

### Post by Jay_Bee on 2008-04-05
Yes, but I don't think that acid3 is weak, its just that developers saw an opportunity to say "We passed the test, we support web standards", it is a very good marketing, and the competition is strong.
Anyway, Firefox 3 will most likely get around 75-80 on its final release, which is still great!
You can monitor their progress here: [http://spreadsheets.google.com/pub?key=pNgBCwWdyRTT2JeiZn4B2Yw](http://spreadsheets.google.com/pub?key=pNgBCwWdyRTT2JeiZn4B2Yw)

---

### Post by PmDematagoda on 2008-04-05
> **tamoneya said:**
> is it just me or has it taken a lot less time for browsers to start passing the acid3 than the acid 2.  I feel like the acid3 wasnt made hard enough and we are already needing acid4.

I guess it's the time in which Acid3 was released, it was during a time when many browsers were still in development so that meant that the developers of those browsers had the time to bring their browsers up to Acid3 standards.

---

### Post by SunnyRabbiera on 2008-04-05
well even if it never passes it firefox will still be my browser, heck acid 2 is still not passed on firefox2 but I still like it

---

### Post by erichmj on 2008-04-06
I'm a bit curious why people think an arbitrary test like the Acid tests even make a difference. I don't care about the results, I just want my chosen browser to work. Passing the Acid tests doesn't mean the browser works any better.

---

### Post by SomeGuyDude on 2008-04-06
Opera beats FF on Acid tests.

Aside from slight differences in text formatting, pages look the exact same in both and I have never, not ONCE, found a page that renders incorrectly in FF but correctly in Opera or vice versa. Thus, I have no idea why the Acid tests should matter to me.

---

### Post by Bachstelze on 2008-04-06
Wow. And beta 4 was at 68%. Impressive. Maybe they'll hit 100% for Firefox 8 :p

---

### Post by pjalegria on 2008-04-07
:lolflag:

---

### Post by bruce89 on 2008-04-07
> **SomeGuyDude said:**
> Opera beats FF on Acid tests.

A few hours later, WebKit passed. You could argue that was the first public pass of Acid 3, as anyone can compile the source.

---

### Post by retrow on 2008-04-07
> **PmDematagoda said:**
> I have just checked out the acid3 test with Firefox3 beta 5 and the result has now risen to[COLOR="Red"] 70/100[/COLOR].

It got to 71/100 when I tested.

[IMG]http://nuclear-imaging.info/files/image/acid3ffx3b5.png[/IMG]

---

### Post by jdong on 2008-04-07
> **bruce89 said:**
> A few hours later, WebKit passed. You could argue that was the first public pass of Acid 3, as anyone can compile the source.


[http://trac.webkit.org/projects/webkit/changeset/31322](http://trac.webkit.org/projects/webkit/changeset/31322)

The way they went about doing it, in my opinion, is anything but honorable.


Also, note that WebKit is in rapid development phase while Firefox is freezing up for a pending release. Some of the changes necessary to pass Acid3 are quite intrusive to the codebase and I, for one, am glad Firefox is sticking to its 3.0 release engineering strategy.

---

### Post by bruce89 on 2008-04-07
> **jdong said:**
> [http://trac.webkit.org/projects/webkit/changeset/31322](http://trac.webkit.org/projects/webkit/changeset/31322)

The way they went about doing it, in my opinion, is anything but honorable.


What's wrong with that?

---

### Post by vexorian on 2008-04-07
His sig?

acid3 tests don't matter that much, I think that there's some sort of important milestone at around 65/100 for a browser to be acceptable, most web devs don't use CSS3 that much...

At this moment Acid2 is what matters more, 3 will become more relevant with time, but it is not too important right now.

Also, I wish no browser needed to pass those two since it is implicit that a browser needs javascript to pass html and CSS standards? wtf?

---

### Post by bruce89 on 2008-04-07
> **vexorian said:**
> His sig??

Actually, this was before the test was passed.

What on earth is the Ahem font?

---

### Post by jdong on 2008-04-07
> **bruce89 said:**
> Actually, this was before the test was passed.

What on earth is the Ahem font?

A specific font requested by the Acid3 test. The default antialiasing behavior of the WebKit rendering engine caused it to fail the test, so they specifically added a workaround so that it'd pass Acid3.


Whatever their reasons for doing this (I've read two justifications of this, usually citing that the specific behavior is not described well enough under the specs), adding a specific acid3 workaround to the codebase is clearly **NOT** the right solution.

---

### Post by bruce89 on 2008-04-07
> **jdong said:**
> Whatever their reasons for doing this (I've read two justifications of this, usually citing that the specific behavior is not described well enough under the specs), adding a specific acid3 workaround to the codebase is clearly **NOT** the right solution.

Indeed it isn't, but temporary workarounds are hardly the worst thing in the world.

If programmers were architects, all the buildings would be destroyed any time a rabbit thumps.

---

### Post by retrow on 2008-04-07
> **bruce89 said:**
> If programmers were architects, all the buildings would be destroyed any time a rabbit thumps.

Only if *rabbit >=0*

---

### Post by tad1073 on 2008-04-07
[http://my.opera.com/desktopteam/blog/show.dml/1862061](http://my.opera.com/desktopteam/blog/show.dml/1862061)

---

### Post by bruce89 on 2008-04-07
> **retrow said:**
> Only if *rabbit >=0*

*rabbit = 0*?

---

### Post by jdong on 2008-04-07
Frankly the only thing gained by what Webkit chose to do is users will go "oooooooh webkit passes Acid3 while your browser doesn't!"

I'm not sure why this is beneficial to the webkit codebase or the Acid3 test's purpose. If there's a deficiency/ambiguity in the specifications that makes some of Acid3's tests defective, that should be addressed. Not masked by a hard-coded specific check in the webkit codebase. There's few excuses for that other than a greedy quest to have the highest test score.

---

### Post by retrow on 2008-04-07
> **bruce89 said:**
> *rabbit = 0*?It was a reality for most part when you consider
*- inf < time < inf*

---


---
title: "Will it work"
date: 2010-05-09
forum: Ubuntu Studio
---

### Post by artyone on 2010-05-09
Completely new to Ubuntu studio and Linux in general.
Got a 9.10, updated, then loaded 10.04, then got the drivers for the graphics.

This was after two previous installs, first without net and second with net but it went wrongish after downloading a plugin  for firefox to download .flv's which may or may not have been the problem.

So third install, got DVD's playing, CD's playing and firefox plays youtubes... all good.

But now I want to get going in some music making starting with Hydrogen... but it won't even go. I've tried reading lots of stuff on jackd but still can't get it to go.

Anyways I went into wine and into configuration and the jack drivers weren't ticked , but the alsa were  so I've ticked the  jack driver and unticked the alsa driver box which had defaultswhen each lined was opened up. Test sound comes up on both or either.

Then when I click control panel  I get a little screen poup that says....

Fix me
X Lauching audio control panel not implemented yet.

I'm supposing wine sits under jack which sits under everything else or am I completely wrong!

---

### Post by cchhrriiss121212 on 2010-05-09
Wine is for running windows programs, and jackd is a native linux sound server so wine is not required right now. What you should do is go to applications>sound>qjackctl, then press the start button.
In 10.04 jack is supposed to work out of the box, but seeing as you upgraded it will probably give you some error messages. Post what comes up and we can go from there.

---


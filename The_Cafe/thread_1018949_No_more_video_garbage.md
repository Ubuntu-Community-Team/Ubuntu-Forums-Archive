---
title: "No more video garbage"
date: 2008-12-22
forum: The Cafe
---

### Post by isaacj87 on 2008-12-22
Apparently, this fix is primarily for Kubuntu users, so I don't know if this would benefit any Ubuntu users. I've noticed that when using KDE 4.1 or 4.2 betas, I get this nasty looking video garbage upon opening programs (even when I minimize/unminimize). This mostly happens with GTK related apps like Firefox. A custom patch to xorg was causing the trouble. Here's a snippet of what Martin Gräßlin said on his blog: 

> Good news to all Kubuntu and Fedora users. The cause for the [video garbage]("http://bugs.kde.org/show_bug.cgi?id=170462") appearing whenever a new window is opened has been discovered. A custom patch to xorg is causing the trouble. Now we can only hope that the distributions will provide updates for xorg without this patch.

A fix has been made available. Someone commented on Martin's blog saying that the patch was probably necessary for *something* and the removal of the patch could cause compositing to suffer. I haven't noticed anything wrong (I'm using an Intel chipset), but your mileage may vary. If you're using the new Nvidia beta drivers, you probably won't need this. If you would like to try and see if this fix works for you, simply add this PPA to your sources.list and upgrade:

```
deb http://ppa.launchpad.net/adamspain/ubuntu intrepid main
```

For those interested in seeing the full blog post, you can find that [here]("http://blog.martin-graesslin.com/blog/?p=211").

---

### Post by Listen2TheTruth on 2008-12-22
Read this post before it gets deleted and my account suspended.

I guess there will always be people who can look at gold and throw it away and think its "fake" or "can't be" or "im an ignorant moron". Pick one of the above im pretty sure you are right up there with any of the above described. 

Ok to clarify. I've build and been using an HHO system in my car for the past 6 months. If anyone can tell you about results, its not a oil lobbied PhD holder, a fake scientist or a opinionated freak who is so paraniod thinking his birth is a conspiracy, no..but someone like me- a regular consumer who has used it and loves it to death!

I drive a volvo that gets 31 MPG HWY with my HHO system off, 53MPG HWY with it on. Any questions? Didnt think so! 

Besides some of you (removed by moderator) forgot that Hydrogen can be extracted from water using electroalysis with solar panels, windenergy etc. so although the extraction process may not be 100% efficient, it sure as hell can be "FREE" if we choose to. 

Oil requires a hell lot of energy to obtain too. Researching, Drilling, Extracting, destilling etc...look at all the processes that it has to go through before it can be made available as a combustable gas. Do some research before you post your ignorant, nonsensical opinions on a topic you have no idea about! 

Do a google search on zero point energy or zero field energy, a guy in kansas invented a device that produces more energy (output)than the energy put into the system to extract it (input). Thats the future of energy "creation" and if you are one of those misleading, good-for-nothing opinionated pinheads thinking "oh matter can neither be created nor distroyed - i learned that in High School...waahhh waahhhh cryyy cryyy" then all i have to say is "you have been living on the moon" for science and technology is a dynamic world and it changes every nanosecond of your existence! So get with the plan and stop being ignorant and crying about a solution that really works!

Lastly, watch ZEITGEIST 1 + 2 and be changed forever.

---

### Post by MikeTheC on 2008-12-23
Yeah, I get that a lot with Firefox (mainly) under Gnome.

But what I wish they'd fix is half to 3/4 of the time whenever I click on something in a window in Firefox in Linux (doesn't happen at all in Mac OS X or Windows) Firefox goes and does something else, like opening a properties display dialog for the link, or trying to email the link to someone, or opening it in a new tab before I get to the point of clicking on "Open in New Tab".

Yeah, I wish to heck they'd fix *that*.

---

### Post by magmon on 2008-12-23
> **MikeTheC said:**
> 

**But what I wish they'd fix is half to 3/4 of the time whenever I click on something in a window in Firefox in Linux (doesn't happen at all in Mac OS X or Windows) Firefox goes and does something else, like opening a properties display dialog for the link, or trying to email the link to someone, or opening it in a new tab before I get to the point of clicking on "Open in New Tab".**

Yeah, I wish to heck they'd fix *that*.

I dont have that problem... Thats odd lol.

---

### Post by TWO on 2008-12-23
> **magmon said:**
> I dont have that problem... Thats odd lol.

Wow lucky you!

That has been one of the consistently annoying things about Firefox under (K)Ubuntu for me...

---

### Post by Skripka on 2008-12-23
> **TWO said:**
> Wow lucky you!

That has been one of the consistently annoying things about Firefox under (K)Ubuntu for me...

Heck I was seeing vid garbage on QT apps...granted with a quick system-you only see it for a second or so--but it is an eyesore to something that is otherwise slick.

---


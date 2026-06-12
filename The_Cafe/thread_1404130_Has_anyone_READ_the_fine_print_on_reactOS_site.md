---
title: "Has anyone READ the fine print on reactOS site?"
date: 2010-02-11
forum: The Cafe
---

### Post by Satoru-san on 2010-02-11
> It would be perhaps important to start by saying what ReactOS -isn't-. It is not another wrapper built on Linux, like WINE. It does not attempt or plan to compete with WINE; in fact, the user-mode part of ReactOS is almost entirely WINE-based and our two teams have cooperated closely in the past.

Soinotherwords, they basically made the interface REQUIRE wine to even run, so it would run REALLY slow.

> 
Other standards such as the Linux Standard Base are often not implemented faithfully. As there is no user interface standard nor a standard API, **most people still have to use command line applications** or fight through the **GUI mess.** Many UNIX derivates use the de-facto standard **X-Window system** for graphical output, **which might well possess one of the worst designs in software history.**

This is making me mad, who do these people think they are?!?!?!

ReactOS has MORE problems, (source: reading the forum), then using Ubuntu~!!!

They also tried to make it look like windows, which isnt that called "COPYING"~!!?

---

### Post by Grenage on 2010-02-11
> They also tried to make it look like windows, which isnt that called "COPYING"~!!? 

Seems fair:

> The ultimate goal of ReactOS is to allow you to remove Windows® and install ReactOS without the end user noticing the change.

---

### Post by koshatnik on 2010-02-11
Why not just install windows?

---

### Post by Satoru-san on 2010-02-11
> **koshatnik said:**
> Why not just install windows?
+1

I dont like windows, but I would rather have people have a working operating system O_O

---

### Post by Nevon on 2010-02-11
> **Satoru-san said:**
> This is making me mad, who do these people think they are?!?!?!
I think you're missing the point. The X Window System IS a garbled mess. Whether or not ReactOS is buggier than random Linux distro is completely besides the point.

---

### Post by Kazade on 2010-02-11
> **Satoru-san said:**
> Soinotherwords, they basically made the interface REQUIRE wine to even run, so it would run REALLY slow.


Erm, not quite. The majority of Wine is a reimplementation of the user-space DLLs that you find on Windows. It makes perfect sense for ReactOS to reuse the open source DLLs that Wine made rather than reimplement the whole thing themselves rather pointlessly. In fact recently they've even started to integrate more of Wine into ReactOS because rewriting Win32 is such a huge undertaking, and Wine has considerably more devs working on it, and Wine's code is more mature (although the lower level you go, the less Windows compatible it is - obviously to deal with the differences between Linux/X and NT).

Also, I don't know why you think Wine would run slow... it runs faster than Windows a lot of the time.

> 
This is making me mad, who do these people think they are?!?!?!


I dislike that paragraph too. A couple of years ago there was definitely an anti-Linux sentiment in the ReactOS team (let's face it, if they loved Linux they wouldn't be reimplementing Windows would they?) but, although the anti-Linux sentiment is still there, it has calmed down a bit recently. I wish they would change that text because it gives a bad first impression about the project. In fact the anti-Linux comments drove me away from their project for a while. 

Still I can't ignore that they are making great progress and if they do finish an open source 100% compatible Windows clone, Windows will lose it's market share over night (the majority of the global Windows install base is pirate). It's not as great as Linux dominating (IMO) but it will have several key advantages over Windows, specifically potentially greater security (faster patch turn around, more bugs found etc.), the ability to package and distribute ReactOS "distros", no dodgy EULA agreements and it's free in both senses of the word.

> 
ReactOS has MORE problems, (source: reading the forum), then using Ubuntu~!!!


It's Alpha software all the way to the core. In fact I wouldn't even class it as Alpha.

---

### Post by Grenage on 2010-02-11
> Windows will lose it's market share over night

> (the majority of the global Windows install base is pirate).

I don't think either of those statements are true ;)

---

### Post by Kazade on 2010-02-11
> **Grenage said:**
> I don't think either of those statements are true ;)

Nope you are right, it's not the majority, but it's a lot: [http://www.osnews.com/img/21035/ballmermacs.png](http://www.osnews.com/img/21035/ballmermacs.png)

I think Windows would take a serious hit if there was a better, faster, more secure alternative with 100% compatibility that was free...

---

### Post by 3rdalbum on 2010-02-11
I happen to think that Xorg is remarkable, and excellent. There are some places where it gets ugly, but it's rapidly becoming better.

However there are some people (Linux users included) who have a bee in their bonnet about X11. Don't get angry, or you'll be angry for long periods of time.

---

### Post by pwnst*r on 2010-02-11
> **Satoru-san said:**
> Soinotherwords, they basically made the interface REQUIRE wine to even run, so it would run REALLY slow.



This is making me mad, who do these people think they are?!?!?!

ReactOS has MORE problems, (source: reading the forum), then using Ubuntu~!!!

They also tried to make it look like windows, which isnt that called "COPYING"~!!?

I like when people get upset for absolutely no reason.

---

### Post by Psumi on 2010-02-11
Some of the devs in ReactOS have said they really hate linux distros, similarly, they dislike windows.

You also have to realize that the command prompt only runs (or rather, it should only run) 16-bit or lower software, and ReactOS is designed to run 32-bit and above. removing the compatibility for the old software is another way to get rid of a security hole.

Apparently, the Win32 API is much more stable than linux' X-Window System due to the fact that A.) X.org can take up to 150 MB of RAM on my system at any given time, while explorer.exe takes up about 10-50 MB at any time. Similarly, the API also makes flash run smoother than in linux, even with the current ReactOS Alpha version, flash for windows already runs pretty well.

Also, as someone said, if you're having problems it is one of these reasons: A.) ReactOS currently is in Alpha and B.) ReactOS is currently made to run more efficiently and smoothly in a Virtual Machine.

Also keep in mind that the x64 version is not ready, by a large margin, but has been worked on recently by a lot.

Once reactOS fixes most, if not all, of the memory leaks, we'll see a lot more speed ups and stability, plus the annoying 47865720 of Virtual RAM and 100% CPU issues gone (hopefully.)

And even though they may be "COPYING" Windows, it is not Windows, nor is it linux. Windows has many a security holes, and ReactOS is built differently to get rid of those, among other problems. Also, Microsoft can't touch the ReactOS Team, at least not very well. (A judge would probably laugh Microsoft out of court if they tried.)

---

### Post by Bachstelze on 2010-02-11
> **Nevon said:**
> I think you're missing the point. The X Window System IS a garbled mess. Whether or not ReactOS is buggier than random Linux distro is completely besides the point.

This.

---


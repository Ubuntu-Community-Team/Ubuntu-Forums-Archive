---
title: "Xgl not in near future"
date: 2005-08-12
forum: The Cafe
---

### Post by poofyhairguy on 2005-08-12
One of the two people working on Xgl just stopped doing it:

[http://lists.freedesktop.org/pipermail/xorg/2005-August/009168.html](http://lists.freedesktop.org/pipermail/xorg/2005-August/009168.html)

It seems that recent hacks to the old system hurt Xgl development:

> 
 The recent work on EXA is going to have the
side effect of pushing out any hope for an Xgl release by a year or
more.  By extending the 2D drivers to accelerate composite end user
demand for Xgl will also be reduced.

Modular X sounds great, and the composite extensions were a nice start, but both kompmgr and xcompmgr are really buggy. Windows ME buggy. And they suck on non Nvidia cards. Hopefully the old 2D solution can become more stable, but it sucks to know that it might be a few years before Linux is the equal to current OSX (when it comes to a elegent OpenGL accerated desktop). I was hoping Xgl would beat out Vista to market....but that might not be the case.

I have one big hope left with Linux Eye Candy- KDE 4 is comming out soon. I hope those guys have some good new ideas. Part of the problem of loving an OS like Linux is that at the low end it might rule (my 300mhz laptop runs much better with Ubuntu than XP) but lags in the high end (my sister's Powerbook feels more responsive- "teh snappy"- than my much more powerful Linux desktop).

Oh well.....this news made me depressed. Time to go play with Luminocity again and pretend it will be in the Gnome release after the next. Sigh.

---

### Post by poofyhairguy on 2005-08-12
If I just said a lot of stuff you dont understand, read this:

[http://www.gnome.org/~seth/blog/relations.html](http://www.gnome.org/~seth/blog/relations.html)

---

### Post by drizek on 2005-08-12
[QUOTE=poofyhairguy]One of the two people working on Xgl just stopped doing it:

[http://lists.freedesktop.org/pipermail/xorg/2005-August/009168.html](http://lists.freedesktop.org/pipermail/xorg/2005-August/009168.html)

It seems that recent hacks to the old system hurt Xgl development:



Modular X sounds great, and the composite extensions were a nice start, but both kompmgr and xcompmgr are really buggy. Windows ME buggy. And they suck on non Nvidia cards. Hopefully the old 2D solution can become more stable, but it sucks to know that it might be a few years before Linux is the equal to current OSX (when it comes to a elegent OpenGL accerated desktop). I was hoping Xgl would beat out Vista to market....but that might not be the case.

I have one big hope left with Linux Eye Candy- KDE 4 is comming out soon. I hope those guys have some good new ideas. Part of the problem of loving an OS like Linux is that at the low end it might rule (my 300mhz laptop runs much better with Ubuntu than XP) but lags in the high end (my sister's Powerbook feels more responsive- "teh snappy"- than my much more powerful Linux desktop).

Oh well.....this news made me depressed. Time to go play with Luminocity again and pretend it will be in the Gnome release after the next (even though all logic in my head tells me it won't because its SOOO slow and buggy now). Sigh.[/QUOTE]

i dont get it. all ive read about exa was that it was just a bandaid they were going to cut out when a "real" replacement came along. they were designing it so taht it could be cut out really easily. oh well, waht do i know? ;)

i tried out the KDE 3.5 livecd today, and it does have some improvements over 3.4. nothing major, just some nice polish here and there. the artwork for KDE 3.5 isnt completed yet, but it looks like its going to be less "KDE"(ie. crystally and blue) than the artwork in 3.4 right now, which is a good direction IMO.

as for 4.0, its going to have some pretty big UI improvements. new kmenu, the whole plasma thing, new splash screens, animations and effects and everything. 

plasma is going to kick ass, it will let you use kicker applets as superkaramba(gdesklets) themes by just dragging them to the desktop, lots of improvements in the system tray and the way kde handles notifications. 

there are a lot of ideas right now, noone really knows for sure what kde 4 is going to look like(which is a good thing IMO). All the work being done now is porting all the current code to QT 4, and removing some of the eyecandy "hacks." things like the kicker can be transparent using kompmngr now, but it makes the whole kicker, text, icons, etc transparent. in KDE 4, it will have real transparency and look much better. 

as for the performance, i have a pretty high-end pc, but i still find linux faster than windows 2k. when i increased my ram from 512 to 1gig, it really helped out a lot in windows. didnt feel a thing in linux(kde and all my apps running only take up about 2/300mb).

---

### Post by poofyhairguy on 2005-08-12
[QUOTE=drizek]
plasma is going to kick ass, it will let you use kicker applets as superkaramba(gdesklets) themes by just dragging them to the desktop, lots of improvements in the system tray and the way kde handles notifications. 
[/QUOTE]

I imagine. KDE has some really neat Eye Candy now. Kompose is cool.

Let me clarify something. I think that currently you can get a high level of Eye Candy. I bought an Nvidia card just for xcompmgr, and its really cool. When I turn it on, things fly. Most Linux box is beating anything I see. Kcompmgr in KDE does the same thing. But it crashes a lot. And its make videos....well....I run it in a terminal so I can turn it off for videos.  But when it works its great. If I could find a way to get rid of Metacity's own compmgr, I'd be set.

Plus I play around gdesklets. And l like the KDE version of those. There is much eye candy if you have the CPU power and the RAM.  And an Nvidia card (ATI's official 2D graphics are pretty bad).

But so many computers don't. So it would nice to milk what people have for all they are worth. Xgl is trying to find a way. 

I was reading a discussion about this, and it was suggested that one reason it might have not gotten big support is that right now official drivers (on Nvidia cards) have the best Opengl. Is the lack of good open drivers for high end cards holding this stuff back?

---

### Post by a-nubi-s on 2005-08-12
This is interesting, coming from Matthias Ettrich.

[Some basic thoughts about KDE4 ](http://blogs.qtdeveloper.net/archives/2005/08/03/some-basic-thoughts-about-kde-4/)

---

### Post by poofyhairguy on 2005-08-12
[QUOTE=a-nubi-s]This is interesting, coming from Matthias Ettrich.

[Some basic thoughts about KDE4 ](http://blogs.qtdeveloper.net/archives/2005/08/03/some-basic-thoughts-about-kde-4/)[/QUOTE]

Cool Read.

---

### Post by drizek on 2005-08-12
[QUOTE=poofyhairguy]I imagine. KDE has some really neat Eye Candy now. Kompose is cool.

Let me clarify something. I think that currently you can get a high level of Eye Candy. I bought an Nvidia card just for xcompmgr, and its really cool. When I turn it on, things fly. Most Linux box is beating anything I see. Kcompmgr in KDE does the same thing. But it crashes a lot. And its make videos....well....I run it in a terminal so I can turn it off for videos.  But when it works its great. If I could find a way to get rid of Metacity's own compmgr, I'd be set.

Plus I play around gdesklets. And l like the KDE version of those. There is much eye candy if you have the CPU power and the RAM.  And an Nvidia card (ATI's official 2D graphics are pretty bad).

But so many computers don't. So it would nice to milk what people have for all they are worth. Xgl is trying to find a way. 

I was reading a discussion about this, and it was suggested that one reason it might have not gotten big support is that right now official drivers (on Nvidia cards) have the best Opengl. Is the lack of good open drivers for high end cards holding this stuff back?[/QUOTE]

kompose is cool, but it is also slow. its going to be rewritten for 4.0 so that it runs smoothly and has some cool animations. 

however, i think you can use the majority, if not all of the eyecandy in linux on a geforce mx440.

TBH, i havent read a lot about xgl, but it does suck its not going to come out soon. on the other hand, exa will be cool :) 

kcomp is very unstable, but i think the majoirty of the problems will be ironed out in 7.0. 6.8.x was the very first release of x.org, so its expected to have problems. 

ya, IMO, drivers are holding everything in linux back. printers, keyboards, mice, sound cards and video cards all perform worse than they should, all because of crappy drivers. its not too bad, but it does not make linux look good when logitech is too lazy to write a driver to make one of their mouse buttons usable. eventually, hardware companies will learn taht it is in their best interest to support linux. all we can do now is to buy from pro-linux companies, and make sure we get as much people using linux as we can.

---

### Post by poofyhairguy on 2005-08-12
[QUOTE=drizek]kompose is cool, but it is also slow. its going to be rewritten for 4.0 so that it runs smoothly and has some cool animations. [/QUOTE]

This made my day.

> 
ya, IMO, drivers are holding everything in linux back. printers, keyboards, mice, sound cards and video cards all perform worse than they should, all because of crappy drivers. its not too bad, but it does not make linux look good when logitech is too lazy to write a driver to make one of their mouse buttons usable. eventually, hardware companies will learn taht it is in their best interest to support linux. all we can do now is to buy from pro-linux companies, and make sure we get as much people using linux as we can.

I try to...

---

### Post by SKLP on 2005-08-12
[QUOTE=poofyhairguy]One of the two people working on Xgl just stopped doing it:

[http://lists.freedesktop.org/pipermail/xorg/2005-August/009168.html](http://lists.freedesktop.org/pipermail/xorg/2005-August/009168.html)

It seems that recent hacks to the old system hurt Xgl development:



Modular X sounds great, and the composite extensions were a nice start, but both kompmgr and xcompmgr are really buggy. Windows ME buggy. And they suck on non Nvidia cards. Hopefully the old 2D solution can become more stable, but it sucks to know that it might be a few years before Linux is the equal to current OSX (when it comes to a elegent OpenGL accerated desktop). I was hoping Xgl would beat out Vista to market....but that might not be the case.

I have one big hope left with Linux Eye Candy- KDE 4 is comming out soon. I hope those guys have some good new ideas. Part of the problem of loving an OS like Linux is that at the low end it might rule (my 300mhz laptop runs much better with Ubuntu than XP) but lags in the high end (my sister's Powerbook feels more responsive- "teh snappy"- than my much more powerful Linux desktop).

Oh well.....this news made me depressed. Time to go play with Luminocity again and pretend it will be in the Gnome release after the next. Sigh.[/QUOTE]
 ](*,)

---

### Post by NoTiG on 2005-08-12
Here is an interesting quote from osnews:

> Xgl is not important
 By vinterbleg on 2005-08-12 14:19:18 UTC
And has never been.
Implementing hardware acceleration at that level is wrong for several reasons. Doing it at composite level provides a much more flexible solution, and you aren't locked in on the OpenGL API.

The modular X.org server with EXA is the way forward.
Cairo with glitz is better than GL-accelerated Xlib, because the Xlib API is over 20 years old, and today's rendering requirements are much better met by Cairo (and Qt4's Arthur, which can also use a GL backend). Xlib is becoming less important, and so the work should be done at the level where it will have any significance.

- Simon. 

Not sure if he is right. but perhaps exa will be good enough?

---

### Post by poofyhairguy on 2005-08-12
[QUOTE=NoTiG]Here is an interesting quote from osnews:

 

Not sure if he is right. but perhaps exa will be good enough?[/QUOTE]

I hope so. At the very least a modular Xorg might make for better drivers!

---

### Post by drag on 2005-08-14
[QUOTE=NoTiG]Here is an interesting quote from osnews:

 

Not sure if he is right. but perhaps exa will be good enough?[/QUOTE]


No he is not right.

XGL/Xegl is as much as a part of a modularlized X.org tree as EXA.

It's kinda stupid actually.

EXA is part of the legacy XFree86 Xserver that we are currently use.. it's a driver framework to replace the extensively flawed XAA driver stuff.

XGL is a different DDX, a different X server.

Just like if you ever used Xnest. Xnest is a X server that runs ontop of a already running X windows setup. So you can do stuff like run Gnome desktop, but run KDE inside the xnest enviroment.

Xnest is a different X server. There are others, too. For isntance there is Xdarwin, which is used by OS X for it's X server stuff. And there are a few legacy ones that nobody touches besides that.

The point of the modularlized X is to keep things like Xlibs and various X applications from being directly dependant on things like the XFree96-style X server.

Right now when you have to upgrade your xserver or some xserver applications you have to download and compile the entire xc tree... which is xlibs, various little x apps and a whole bunch of other things.

This is why Debian has had such a hard time keeping up with X releases in the past. Because they do gradual updates instead of all-in-one-big-leap style updates, by dealing with a monolithic situation the entire transition from one X version to another one had a huge system-wide disruptive effect. Everything needed to be recompiled, retesting, mirrors distributed with the new information and all that. Debian had a hard time coping with it.

What EXA is designed to do is to extend the life of the XFree86 style X server and make things like RENDER work properly so that composition works quickly and is stable... I figure if they didn't do that then it would set back the eye candy stuff another couple X releases till Xegl stabilises.

Right now everybody is working on modularlizing X.org and all that. The next release will be dual-natured... a 6.9 release and a 7.0 release.

The 6.9 release will be the legacy-style monolithic xc-style release. The 7.0 will be the new autotooled and modularlized X.org of the future.  They will be both using the same code and everything, but it's designed as a transitional release... So that it would be much easier to go from a monolightic style X system to a modularlized X system. 

to see more:
[http://wiki.x.org/wiki/](http://wiki.x.org/wiki/)

I think that they are actually behind schedule on this release by a bit.. which is probably partially why XGL isn't getting the love it needs. Maybe after this release more developers will be able to spend more time on Xegl.

But of course that remains be seen.

Keep in mind that for XGL/Xegl to ultimately to succeed it's going to be very dependent on modular X anyways. Plus Xegl, which is the standalone Xserver that they are working on, depends on Glitz for it's functioning...

Glitz replaces RENDER... one of the major reasons that EXA is being developed is to make RENDER run better... That's a bit redundant, don't you think?

I hope that XGL/Xegl has just been put on the back burner and is not dead though. It would suck to loose something with such promise.

See
[http://www.waimea.org/wiki/Xegl](http://www.waimea.org/wiki/Xegl)
for details.



edit:
Note that that was probably littered with innaccuracies. This is just my personal understanding on the subject.

---

### Post by TristanMike on 2005-08-14
[QUOTE=poofyhairguy]If I just said a lot of stuff you dont understand, read this:

[http://www.gnome.org/~seth/blog/relations.html](http://www.gnome.org/~seth/blog/relations.html)[/QUOTE]I'd like to go, but I can't get gnome.org to load in my firefox....for quite some time now, I just thought it was down or something, any suggestions, I wanted to read over all the linux stuff I could but I can't get there anymore.....any help?

EDIT: The operation times out when trying to connect, that's the error, don't know how to troubleshoot.

---

### Post by cowlip on 2005-08-14
[QUOTE=TristanMike]I'd like to go, but I can't get gnome.org to load in my firefox....for quite some time now, I just thought it was down or something, any suggestions, I wanted to read over all the linux stuff I could but I can't get there anymore.....any help?

EDIT: The operation times out when trying to connect, that's the error, don't know how to troubleshoot.[/QUOTE]
 If you use    System->Network Tools, can you ping gnome.com?

---

### Post by Cossins on 2005-08-14
[QUOTE=NoTiG]Here is an interesting quote from osnews:

 

Not sure if he is right. but perhaps exa will be good enough?[/QUOTE]
 Heh, yeah, that was me. :)

drag: Glitz does not at all replace RENDER, those are two completely different things. If anything, GLX replaces RENDER.

And I do stand by my original statement, that implementing Xlib on top of GLX is suboptimal, though interesting. Partly because GLX in most situations depends on proprietary drivers that don't always work as they should (the Linux ATI drivers are a good example), and many OSS drivers have 2D acceleration but not 3D acceleration (like nv).

So, the ideal solution is the ability to choose freely between rendering and acceleration backends. Now I'm not quite sure here, but from what I gather, EXA will enable us to use whatever kind of acceleration fits the current driver best.

XGL should be seen as a similar attempt as the original xserver/kdrive, an experimental playground for new technology and fun experiments, not something that will come to practical use in the mainstream.

- Simon

---

### Post by TristanMike on 2005-08-14
[QUOTE=cowlip]If you use    System->Network Tools, can you ping gnome.com?[/QUOTE]I'm sorry, how do I ping? I can see gnome.com, I can't see gnome.org(ya probably meant that, but I thought I'd clarify, just to be sure)

---

### Post by poofyhairguy on 2005-08-15
[QUOTE=Cossins] many OSS drivers have 2D acceleration but not 3D acceleration (like nv).[/QUOTE]


Is that a bigger reason why Linux Eye Candy is developed so slowely?

---

### Post by charlieg on 2005-08-15
Jon has invested too much time and effort to just stop.  Hopefully a bit of a rest will see him return invigourated and he and Dave Reveman will get some help post-modularisation of Xorg.

I agree with drag's assessment.

Cossins: running xlib on xegl is not sub-optimal.  Your argument is flawed.  "Proprietry drivers have bugs."  Well then we're screwed either way.  Hopefully Ati will wake up.  If not, we'll end up with people improving the FOSS drivers.  "FOSS drivers don't support acceleration."  Well that's just not true, although they're not as optimised as the proprietry versions.

---

### Post by poofyhairguy on 2005-08-16
[QUOTE=charlieg]  Hopefully Ati will wake up.  [/QUOTE]

I hear they will make better drivers after the modular Xorg comes around. Won't help that they have always sucked with opengl though.

---


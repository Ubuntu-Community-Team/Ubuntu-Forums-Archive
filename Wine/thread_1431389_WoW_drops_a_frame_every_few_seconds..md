---
title: "WoW drops a frame every few seconds."
date: 2010-03-16
forum: Wine
---

### Post by awinterbreeze77 on 2010-03-16
Yes, another WoW post. 

Game runs like a charm, except for one weird thing. It skips a frame every 2 seconds or so.

I'm running Hardy Heron on a Macbook Pro 1,1. My graphics card is an ATI Radeon x1600 Mobility ... or something like that.

Any thoughts? I'm running it using OpenGL, of course.

---

### Post by Tikkyca on 2010-03-16
You should try putting settings a little lower on your driver.

---

### Post by awinterbreeze77 on 2010-03-17
Well, I should say that the game runs smooth, it's just that everything skips a frame. So it's not a FPS drop. The FPS is maintained, it's just, well, a frame is skipped.

But, how do set my driver settings lower?

If you mean setting the values lower within game, I've already tried that...

Thanks!

---

### Post by spoons on 2010-03-18
Is your hard disk accessing at this point?

---

### Post by peacewithall on 2010-03-18
I had this problem, WoW would skip and stutter for a second, within several seconds of each other. My problem was BOINC, it performs pretty bad in Ubuntu last couple of releases, and started bad in 9.04, and still is in 9.10, solution was to pause it. Although now a new version of BOINC, 6.10.36, features a new option to suspend computation when the CPU usage is above 25% (default), I set mine to 23% on my quad core system(you might need to experiment with that to find the right setting).

Of course you might not have BOINC, which would mean something is running and using the CPU every so often, keep an eye on system monitor and see if anything else is running high during gameplay.

---

### Post by awinterbreeze77 on 2010-03-19
>  		Is your hard disk accessing at this point? 	
You mean when it skips? I don't think that that is what is causing the problem... there are times in low traffic areas, I'm just starting to notice, that there is no frame-skipping whatsoever. Like, if I look straight at the ground and zoom all the way in. So even if it was the HD accessing causing the skipping, it seems like it would make it skip all the time.

As for BOINC, I'm not sure if I have it, but I will have to look into to it. I've noticed one more odd thing, believe it or not. If I somehow minimize WoW or move to a different desktop while it is still running, I notice that the mouse pointer for my computer also 'skips frames' as well! I'm starting to believe that this must be a performance issue and somehow the skipping frames thing (instead of just an FPS drop) is the stopgap measure that my computer is using. This leads me to believe that it must be a performance issue, although lowering the settings in-game as availed me none.

Hmm...

---

### Post by awinterbreeze77 on 2010-03-19
K, I checked the system monitor and not much is going on there. It's simply Wine at the top of the list, with a CPU Usage % of 13 as I let WoW idle at the login screen, and then 1 % from the System monitor, and then 0% from everything else.

I'm wondering if my ATI video card is the cause of all this.. and if so, if there's anyway to fix it.

---

### Post by awinterbreeze77 on 2010-03-19
Okay, so update: I fixed the problem largely by turning down the graphics ALL the way (I mean, putting everything at super super low graphix) and then turning 'Reduce Input Lag'. Unfortunately, this has created more problems, namely the lack of the interface working o_o properly all the time. Oh well, what can you do, heheh. 

Still, I wonder why the graphics have to be down so low, and if there is a better fix for this.

---

### Post by Brebs on 2010-03-20
> **awinterbreeze77 said:**
> skips a frame

Use a decent kernel scheduler - [BFS](http://ck.kolivas.org/patches/bfs/).

[pf](http://postfactum.pl.ua/pf/) is a convenient patchset.

---

### Post by awinterbreeze77 on 2010-03-23
Update: Ok all, so here is a quick update on my progress with this. You could consider this problem partially solved, I guess.

The problem seems to revolve around performance issues, but a huge part of it seems strangely to be invested in resolution. I don't know exactly how it happened, but I went from skipping like mad while I played to much less skiping by setting my resolution to 800x600 and turning off Specular Lighting and Texture Mapping. I've noticed that while tweaking the other settings up a bit CAN cause the same drop a frame issue, often it does not, and I've been able to play with medium settings in all of the other categories instead of just bottom of the barrel low. 

Haven't tried bfs or pf yet.

---

### Post by Brebs on 2010-03-23
> **awinterbreeze77 said:**
> Haven't tried bfs or pf yet.
The sad reality is that NO amount of in-game tweaking can fix a horribly-bad kernel scheduler. Trust me, I've spent [far more time than reasonable](http://forums.gentoo.org/viewtopic-t-701119.html) on this.

The recent kernels have had [horribly-bad kernel schedulers](http://ck.kolivas.org/patches/bfs/bfs-faq.txt).

Fix your kernel FIRST, not last.

---


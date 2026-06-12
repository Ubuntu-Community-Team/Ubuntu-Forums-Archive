---
title: "Running WoW on Wine, problems galore"
date: 2009-02-17
forum: Wine
---

### Post by kenaro on 2009-02-17
So, I'm new to Ubuntu, for the most part. I'm trying to run World of Warcraft on my Wine system; I've followed all the step on the wiki and community, I've followed all applicable troubleshooting, and I'm still unable to run WoW without getting, first, graphics vomit in the WoW window and, second, a black-screen crash if I don't close the window within a couple of minutes.

I've looked everywhere, and I can't find a fix for this. Anyone had this problem, and have a good fix?


(Running Ubuntu 8.10, Wine 1.1.14)

---

### Post by kenaro on 2009-02-17
Apparently, there's not a single person on the whole internet that can tell me what's wrong with this. -_- I've asked friggin everywhere.

---

### Post by hikaricore on 2009-02-17
Please provide info on your system.  CPU, RAM, video hardware/drivers.

So far you've given us nothing to go on. :p

---

### Post by kenaro on 2009-02-19
> **hikaricore said:**
> Please provide info on your system.  CPU, RAM, video hardware/drivers.

So far you've given us nothing to go on. :p
Oop! My bad, I thought I copy/pasted that in when I made the thread. ^.^; Looks like I only grabbed the Wine/Ubuntu info.

I'm on a Sony Vaio VGN-NR110E, 2.5 GB of RAM, and.. my terminal pulls up..

Intel(R) Pentium(R) Dual  CPU  T2310  @ 1.46GHz

VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller

So. :D

[B][B]
(Edited to included processor info)[/B][/B]

---

### Post by kenaro on 2009-02-19
Quite honestly, I don't know where to check my drivers, though. I know the commands, but I don't know what information is the drivers, and what is the hardware.

---

### Post by panaut0lordv on 2009-02-19
Is your blackscreen crash similar to this one? [http://ubuntuforums.org/showthread.php?t=1073299](http://ubuntuforums.org/showthread.php?t=1073299)

---

### Post by kenaro on 2009-02-19
> **panaut0lordv said:**
> Is your blackscreen crash similar to this one? [http://ubuntuforums.org/showthread.php?t=1073299](http://ubuntuforums.org/showthread.php?t=1073299)

In that the screen scrambled itself and then went black with no response from ctrl+alt+backspace, yes. Black screen with nothing but an X shaped cursor, and even that disappeared after a couple of minutes.

However, I haven't even reached the character screen prior to a crash.

---

### Post by panaut0lordv on 2009-02-19
You should try to install propetiary driver for your graphics from [http://downloadcenter.intel.com/default.aspx?iid=gg_work+home_dowloads#](http://downloadcenter.intel.com/default.aspx?iid=gg_work+home_dowloads#)
Maybe it's going to work better than free one.

---

### Post by kenaro on 2009-02-19
> **panaut0lordv said:**
> You should try to install propetiary driver for your graphics from [http://downloadcenter.intel.com/default.aspx?iid=gg_work+home_dowloads#](http://downloadcenter.intel.com/default.aspx?iid=gg_work+home_dowloads#)
Maybe it's going to work better than free one.
Honestly, I might need to know exactly where to go, and what/how to download/install. >_>;

---

### Post by panaut0lordv on 2009-02-19
OK, after looking at this site there's no propetiary driver like nvidia has. Then you probably have it installed.

> INTEL issues

 Unfortunately, Intel does not make its own drivers for their cards for Linux. Their Windows drivers aren't even that good to start with.

For World of Warcraft to work properly, you need to look for an Open Source Intel Driver that gives you direct OpenGL rendering support.

-----

There are no known Issues with Intel Cards, apart from bad FPS on certain drivers.
---- 

---

### Post by kenaro on 2009-02-19
> **panaut0lordv said:**
> OK, after looking at this site there's no propetiary driver like nvidia has. Then you probably have it installed.

Any leads at all on where I cold find that open source driver?

---

### Post by kenaro on 2009-02-20
Actually.. if someone could hook me up with some terminal prompts to directly download and install, that would be the ultimate awesome.

---

### Post by Twitch6000 on 2009-02-20
> **kenaro said:**
> Any leads at all on where I cold find that open source driver?

Uhmm your driver is already installed...

Try running WoW in opengl mode there is a howto here on the forums and winehq

---

### Post by kenaro on 2009-02-20
> **Twitch6000 said:**
> Uhmm your driver is already installed...

Try running WoW in opengl mode there is a howto here on the forums and winehq

I actually have already. Just made me crash faster.

---

### Post by kenaro on 2009-02-23
After a weekend of testing and debugging, I still fail to run WoW...

---

### Post by kenaro on 2009-02-26
So, I've given up at this point on getting WoW to run on my machine without spending a small fortune on hardware.. so I'm converting back to Windows, and just getting XP instead of Vista. Thanks for all you guys that tried to help.

---


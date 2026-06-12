---
title: "Gutsy vs. SunBlade 100"
date: 2007-05-31
forum: Sun Sparc Users
---

### Post by jdeisenberg on 2007-05-31
I downloaded gutsy-alternate-sparc.iso, build of 31 May 2007, and tried to install on SunBlade 100 with 256M.  It gets to the "Booting Linux" prompt and hangs (same behavior as 6.10).

Feisty installs fine, but doesn't let me do X (mmap error). My goal is to get the X server to work. If I can get xorg from a repostiory for gutsy and install that on the Feisty system that might do the trick.  A repository URL for sources.list would assist greatly; thanks.

---

### Post by netztier on 2007-06-01
> **jdeisenberg said:**
> 
Feisty installs fine, but doesn't let me do X (mmap error). My goal is to get the X server to work.

What about installing Feisty (just the minimal stuff), and then changing the sources.list to refer to the gutsy repos and doing the aptitude dist-upgrade? Like this you could upgrade to Gutsy without the CD-ROM boot hassle.

BTW.. have you tried passing **ide=nodma** as boot parameter for the installation kernel when booting from CD?

best regards

Marc

---

### Post by jdeisenberg on 2007-06-01
The upgrade is a good idea. Yes, I did use the ide=nodma, to no effect.

---

### Post by chris_andrew on 2007-06-05
I've also heard that using the X package from Debian's Etch works around the problem.

---

### Post by jdeisenberg on 2007-06-06
I did the full upgrade...and ended up with a system that hangs at "booting Linux..."

I'll try a less extreme version, by upgrading only X. The question is how much I have to upgrade (specifically, which packages: X, X server, and which of its adjuncts and subsidiaries).

---

### Post by jdeisenberg on 2007-06-13
OK. I did get it to work. For the record, here's what I did:

1) Reinstalled Ubuntu 7.04
2) Changed [FONT="Courier New"]/etc/apt/sources.list[/FONT] to use the unstable version of Debian:
```
deb http://mirror.anl.gov/debian/ sid main
```
3) Created a file called [FONT="Courier New"]15changecache[/FONT] in folder /[FONT="Courier New"]etc/apt/apt.conf.d[/FONT] with this line:
```
APT::Cache-Limit 33554432;
```
4) Did an [FONT="Courier New"]apt-get update[/FONT] followed by [FONT="Courier New"]apt-get install xserver-xorg[/FONT]
5) In order to avoid having the monitor go out of sync range, I had to add a line to the "Device" section of  [FONT="Courier New"]/etc/X11/xorg.conf[/FONT] 
```
Option "ReferenceClock" "29.5000MHz"
```
6) Restored [FONT="Courier New"]/etc/apt/sources.list[/FONT] to its former state, and re-ran [FONT="Courier New"]apt-get update[/FONT]

---

### Post by cantormath on 2007-06-15
How does feisty or gutsy work on the sunblade?  I was looking into trying it out.

---

### Post by jdeisenberg on 2007-06-15
> **cantormath said:**
> How does feisty or gutsy work on the sunblade?  I was looking into trying it out.

Pretty well. When I log in, I get a dialog box telling me that hald couldn't be started, and there were some instances where a window didn't erase properly, but without further testing, it could be just a "once-only" occurrence.  Overall, I'm pleased with the results. (These are machines which would otherwise have been declared as surplus, and will now be usable in the engineering department at the community college where I teach.)

---

### Post by cantormath on 2007-06-15
I am working on a similar project with sunblade 100's.  Do you have any recommendations.  How much ram are you using?

Thanks for the response.

---

### Post by jdeisenberg on 2007-06-15
> **cantormath said:**
> I am working on a similar project with sunblade 100's.  Do you have any recommendations.  How much ram are you using?

Thanks for the response.

I was using 128MB, and it was having problems, so I moved the test machines up to 256MB (by stealing memory from one machine and installing it in another one).  You can get 256MB modules from Memory 10 ([http://www.memoryx.net/](http://www.memoryx.net/)) for $40. You probably know this already, but don't buy regular PC memory; you need ECC memory.

I have a document that tells what I've done; when I can post it I'll put the URL on this forum.

---

### Post by netztier on 2007-06-16
> **jdeisenberg said:**
> Pretty well. When I log in, I get a dialog box telling me that hald couldn't be started, and there were some instances where a window didn't erase properly, but without further testing, it could be just a "once-only" occurrence. 

On my U60 with the creator cards, I have the same problem. In the end, GNOME is almost unusable without hal.

Panels don't load properly, panel applets aren't visible, windows don't get updated - impossible to work like that.

I went back to 6.06LTS, but haven't yet re-installed any of the desktop packages.

regards

Marc

---

### Post by cantormath on 2007-06-18
> **jdeisenberg said:**
> I was using 128MB, and it was having problems, so I moved the test machines up to 256MB (by stealing memory from one machine and installing it in another one).  You can get 256MB modules from Memory 10 ([http://www.memoryx.net/](http://www.memoryx.net/)) for $40. You probably know this already, but don't buy regular PC memory; you need ECC memory.

I have a document that tells what I've done; when I can post it I'll put the URL on this forum.

I definitely look forward to your notes.  The Error Correction Controlled ram is a pain and more expensive, so I will probably have to go about getting more ram the same way you did.

---


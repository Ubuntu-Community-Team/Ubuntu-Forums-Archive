---
title: "wine wow FPS patch"
date: 2011-02-17
forum: Wine
---

### Post by ngsupb on 2011-02-17
WOW funs will like this patch. Need some testers :p

I will share the patch I found. For those who have appropriate knowledges to patch wine, here is the patch that adds support for multi-core processors, increasing wow performance to the same level as directX on windows.

[bugs.winehq.org/show_bug.cgi?id=11674#c64]("http://bugs.winehq.org/show_bug.cgi?id=11674#c64")

Please note it is beta though, but worked for me except of a few times with segfault error.

---

### Post by Tweak42 on 2011-02-18
Well what better way to learn how to patch and build from source. :-)

I got the source from the ubuntu PPA, applied the patch and compiled.  Starting from a clean .wine prefix frame rate is noticeably faster flying around Stormwind.  Biggest difference I can quantify using the System Monitor is that both cores are hitting steady around 95% instead of fluctuating 60-80%.  I did segfault a few times at the loading screen and when taking a portal.

This was run on my desktop system, Core2Duo 3.0ghz, Nvidia GTX560, 4GB memory.

---

### Post by Tweak42 on 2011-02-22
I tried using this over the past few days and it's to unstable for normal use.  Most of the segfaults happen when taking a portal, or traveling to a different region/zone.  Otherwise it's holds much promise in improved performance in upcoming wine versions.

---

### Post by Tweak42 on 2011-03-10
Good news follow up:

Thanks to Dmitry post [http://bugs.winehq.org/show_bug.cgi?id=11674#c71](http://bugs.winehq.org/show_bug.cgi?id=11674#c71) I'm now able to play using the patched wine almost stable.  The tip that worked for me was turning the texture detail to minimum.  

I have run at least three 5 man heroics and taken numerous teleports without crashing.  If you do teleport somewhere try not to move immediately and wait a moment for objects to load. I haven't tried any raids or large scale battlegrounds yet.

Note: this was using wine compiled on my desktop system, on my laptop  performance did not improve in busy areas, likely because of bottleneck graphics chip.

---

### Post by Tweak42 on 2011-03-24
Update: Latest rgl patch fixed the graphical artifacts and I can up the texture quality without crashing.  I've only run it a few hours, but no crashes or long pauses yet.  

Frame rate jumps from 20fps to 40fps in areas with many objects (busy city) and or wide open area with much detail in distance (twilight highlands and hyjal).  I booted into windows7 to compared and performance seems about even.

Hardware: Core2Duo E4300 @ 3Ghz, Geforce GTX460 756mb, 4gb ram

---

### Post by frriction on 2011-03-26
Is this patch for latest beta or stable version. Should I use -p0 or -p1 ?

---

### Post by Tweak42 on 2011-03-28
> **frriction said:**
> Is this patch for latest beta or stable version. Should I use -p0 or -p1 ?

I used the latest beta 1.3.16.  
The -p0 or -p1 switch is to designate how 'patch' handles relative directory pathing when apply any patch files.  Open rgl.patch file in text editor and you can see the directory path follows along the lines "diff --git **a/dlls/kernel32/process.c** b/dlls/kernel32/process.c"

So if you run "patch -p0 < rgl.patch", patch will use the entire path looking for the files to modify. (a/dlls/kernel32/process.c)
"-p1" ignores up to the first "/"  (dlls/kernel32/process.c)
"-p2" would ignore up to second "/" (kernel32.process.c)

If I'm not clear enough, try looking up -pnum switch using "man patch" documentation.

---

### Post by Tweak42 on 2011-04-12
Custom Wine PPA with the patches available for testing (courtesy of Aigars Mahinovs) 

[https://launchpad.net/~aigarius/+archive/aigarius-winepulse](https://launchpad.net/~aigarius/+archive/aigarius-winepulse)

For me it still crashes occasionally, usually right after loading screen / flying across zones lines or regions.  It's never has crashed in a fight, instance or raid.  Works well enough that I use it normally.

---

### Post by frriction on 2011-04-12
I have tried that ppa couple of days ago. WOW doesn't launch at all. It shows some error not sure what it ask me report the error to blizzard. 
It seems like wow.exe has problem with compiled wine from that ppa.

Or I haven't installed wine component.

---

### Post by samuaz on 2011-07-08
> **frriction said:**
> I have tried that ppa couple of days ago. WOW doesn't launch at all. It shows some error not sure what it ask me report the error to blizzard. 
It seems like wow.exe has problem with compiled wine from that ppa.

Or I haven't installed wine component.

+1

Yesterday compile wine from source, including the patch rgl, and have problem with wow.exe, the error occurs when executed, access error in the reading and writing RAM.

without the patch does not cause the error but I would like to improve fps using the patch.

any ideas?

---

### Post by Tweak42 on 2011-07-09
I'm currently using the patched wine+pulse 1.3.22 from the PPA and it's pretty stable for me.  Before I was using 1.3.19 with rGL patch complied from source and it ran slightly less stable.

I'm not sure if it makes a difference, but I create a clean wine prefix each wine version then attach my wow directory to it.

---

### Post by Tweak42 on 2012-02-09
**This is for users who are interested compiling wine with the rGL patch and want instructions all in one place.**

**Assumed prerequisites:**
[LIST]
[*][Ubuntu Wine Team PPA]("https://launchpad.net/~ubuntu-wine/+archive/ppa") enabled
[*][http://www.aewi.info/rgl/rgl.patch.gz](http://www.aewi.info/rgl/rgl.patch.gz) extracted to home directory
[*]Wine build dependencies:
[/LIST] ```
sudo apt-get build-dep wine1.3
```

**Terminal commands:**
Download the wine source:
```
apt-get source wine1.3
```
Change into the newly created directory.
```
cd wine1.3-<wine version>
```
Apply rGL patch; any patching errors should show up here.
```
patch -p1 < ../rgl.patch
```
Create the make file; any dependency errors should show up here.
```
./configure
```
Compile the code; this takes the longest time.
```
make
```
If everything completes ok, you can run the newly created binary by:
```
./wine <path to your wow.exe>
```

For wine newbies, this is a separate version of wine created in your home directory, so to remove it just delete the wine files and the wine directory in your home directory.

Compiled for wine1.3-rc5, Nvidia 290.10 drivers; Ubuntu 10.10, 11.10
Stable enough for LFG raiding, but I have experienced minor graphical glitching.

---


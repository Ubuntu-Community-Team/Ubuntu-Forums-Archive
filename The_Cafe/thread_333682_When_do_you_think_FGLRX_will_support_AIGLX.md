---
title: "When do you think FGLRX will support AIGLX?"
date: 2007-01-07
forum: The Cafe
---

### Post by Patrick-Ruff on 2007-01-07
This has been a recurring issue that has been bothering me for quite some time. I have an ATI X300 PCIe that has to use FGLRX to have any acceleration whatsoever, and I really don't think it's very effecient or even working fully.  regardless, FGLRX does not support AIGLX. or maybe it's the other way around (I doubt it.)  

Do you think Feisty Fawn will have new technologies that allows FGLRX or cards like mine to run AIGLX flawlessly?  the open source ATI Drivers only have experimental 3d acceleration, which doesn't work well at all. and don't even get me started on XGL . . . I think it goes without saying how horrible it is . . .


so, post your opinions.  don't try to help me because I'll guarantee you I've tried everything.
and don't limit your self to fact and what you know is going to be released in the future, I'd like to hear what I haven't heard yet, and I'm sure other members of this forum are interested as well.

---

### Post by jdong on 2007-01-07
When I purchased my laptop, I made the decision that I was willing to accept an ATI card (mobility x1400) in return for all the other features it will provide me and the good general Linux compatibility.

Currently, I'm running Beryl, fglrx + xgl without much issue. There were a few annoyances (DPMS monitor shutoff, backspace / shift+backspace keys) that I had to work around, but overall it's working.

As far as fglrx and AIGLX / indirect rendering, I really don't know when it'll happen; only ATI/AMD would. I don't really want to go into any ATI or any other vendor bashing, but the AIGLX rendering stack is still relatively new.

---

### Post by commike37 on 2007-01-07
I think it will take an especially long time to get this kind of compatibility with my card, the XPress 200M.  It took a long time for even ATI to make a driver that can deal with that card (or at least since 8.24.8 from what I've heard).

---

### Post by jdong on 2007-01-07
The entire Radeon Xpress line has a terrible record with all non-Windows 2K/XP operating systems.

---

### Post by Patrick-Ruff on 2007-01-08
in my experience, XGL is far more unstable then AIGLX.  Aiglx being built into xorg 7.1, it just seems much better in every way.  forgive my ignorance for I don't know the actual specifics. but doesn't AIGLX offer full application GTK acceleration rather then just window boarders or something like that?

---

### Post by BOBSONATOR on 2007-01-08
I use XGL with my Beryl and the preformance is amazing on my laptop

Centrino 1.8
512 DDR
ATI9000 Mobility (on fglrx)
ipw2200

---

### Post by adam.tropics on 2007-01-09
I have been strangely lucky in that my RadeonXpress 200m has worked fine since Breezy...can't remember the ATI release number. 

Personally, I have come to accept that ATI are closed source, and frankly if it works, I can live with that. However, I find it immensely irritating that there is also no dialog between ATI Linux developer(s) and users. Whether they open the source or not, an ongoing, 'suggestions taken seriously' approach would be nice. At least in such an environment, we would have an idea of intent to 'perhaps' support AIGLX.

---

### Post by matthew on 2007-01-09
> **BOBSONATOR said:**
> I use XGL with my Beryl and the preformance is amazing on my laptop

Centrino 1.8
512 DDR
ATI9000 Mobility (on fglrx)
ipw2200I've been doing the same with very similar hardware (Mobility Radeon 9700) and similar results.

---

### Post by pormogo on 2007-01-11
Who knows, getting ATI to support open source is like trying to pull a tigers teeth. I too have been running fglrx+XGL+beryl and disliking it greatly. Xgl is ok but it has it's share of issues (higher CPU time, shift backspace issues, no 3d acceleration REALLY hurts). I would hope that ATI can get around to supporting compositing SOMETIME this year.

---

### Post by jdong on 2007-01-11
(1) Xgl, though using more CPU, runs significantly smoother with Beryl than NVidia's AIGLX implementation at least on my low-power Geforce4 MX400's. Full-screen videos in fact drop frames without using Xgl on these cards.

(2) Shift-backspace is really easy to correct: xmodmap -e "keycode 22 = BackSpace"

(3) Launch 3D fullscreen apps (like games) with DISPLAY=:0 (i.e. to the parent display) and they'll work full-speed. This workaround should get you by with most gaming needs. However, windowed 3D programs are a different story. AIGLX+beryl isn't exactly blazing fast with those either, but does provide an easier way to shut off Beryl without losing work.

(3) AIGLX has out-of-the convenience that cannot be beat! For that, I will not try to make an Xgl counter argument :D

---

### Post by TusharG on 2007-01-13
You may want to check this link...

[http://www.phoronix.com/scan.php?page=article&item=623&num=1](http://www.phoronix.com/scan.php?page=article&item=623&num=1)


New ATI 8.33.6 is releasing soon we may get a fix in the build.

---

### Post by jdong on 2007-01-13
I'm already running 8.33.6.... feels exactly the same; it just adds preemptive support for the new Radeons about to come out.

That's a pretty good sign actually, that ATI is adding support for the R600 chipset before it even releases -- compared to the R500's which took nearly half a year after release to get Linux drivers!

---

### Post by Luciano on 2007-01-14
Hi all, i have spent a lot of time using Beryl with XGL & AiGLX with the fglrx & radeon drivers and have found out the following using a X800 XL card:

1. ATi have recently been making big strides in there driver support for non-M$ OSes, and i think they are starting to make things right again in this department, but they still have a long way to go to meet the needs of the linux community. Give it another 12 months and i think ATi will have drivers as good as the Nvidia or Intel ones.

2. XGL is a 'hack' and always will be. This is a major reason it is not completely stable or easily maintaind. When Xegl is released XGL will become obsolete.

3. AiGLX is **not** a 'hack' as it conforms to the Xorg standards. Which is why it is inherantly more stable than XGL.

4. fglrx/XGL/Beryl - with this combination on my X800 XL card i was able to get about 550fps with little tweaking of the Xorg.conf file.

5. radeon/AiGLX/Beryl - with this combination i can get about 500fps with with lots of tweaking of the Xorg.conf file. Before tweaking the conf file i only got about 150fps. I also manged to get Dual Monitors working easily aswell, alough there is another error related to this that isn't driver specifc but card related. See point 6.

6. Most ATI card have a MAX TEXTURE SIZE of 2048x2048 in OpenGL, this means that you can only have a desktop size of 2048x2048 (e.g. 2 monitors @ 1024x768 each) if the resolution is larger than 2048x2048 then you will get a section of the desktop that is missing a background image aswell as other funnies that happen. I think i read somewhere this is part of the firmware on ATI cards and hence cannot be fixed with a driver update. Someone correct me on this if it's incorrect.

As you may have noticed tha radeon drivers are only 10% slower than the fglrx ones provided you have the correct options set in the xorg.conf file. I am happy to sacrifice this 10% for the added stability and benifits of AiGLX. I hope this helps people make an informed decision on XGL/fglrx or AiGLX/radeon debate.

---

### Post by Patrick-Ruff on 2007-01-16
"3. AiGLX is not a 'hack' as it conforms to the Xorg standards. Which is why it is inherantly more stable than XGL."

umm, it's not a hack because it's built into xorg 7.1 dude.

"5. radeon/AiGLX/Beryl - with this combination i can get about 500fps with with lots of tweaking of the Xorg.conf file. Before tweaking the conf file i only got about 150fps. I also manged to get Dual Monitors working easily aswell, alough there is another error related to this that isn't driver specifc but card related. See point 6."

my card isn't supported enough by the open source drivers to have good 3d accel, it's only "expiremental" therefore, I get very litttle accel with the x300.

---

### Post by EdThaSlayer on 2007-01-16
The first problem from my opinion is that they need to fix "fgrlx" properly so that it can compete with the Nvidia drivers(compare a Geforce 2 1000 fps against my 9600 that has 1500 fps, big difference in performance and BIG difference between the price of these two[fyi:I actually tested this]).

---

### Post by luca.b on 2007-01-16
Call me pessimist, but I'd say "never" or close to never. ATI drivers are always terrible, and not only on Linux (I remember the pain when I still used Windows). 
Personally I'd like (though I don't think it's likely to happen soon) them to fix the hibernation issue first, so I can finally hibernate/resume without problems on my lapotp (everything else works, but fglrx causes screen corruption, so...)

---

### Post by jdong on 2007-01-16
> **EdThaSlayer said:**
> The first problem from my opinion is that they need to fix "fgrlx" properly so that it can compete with the Nvidia drivers(compare a Geforce 2 1000 fps against my 9600 that has 1500 fps, big difference in performance and BIG difference between the price of these two[fyi:I actually tested this]).

Don't use glxgears as a benchmark -- it's not. Minor changes in driver architecture can dramatically affect glxgears FPS while not rendering any difference in real-world applications.

---

### Post by PriceChild on 2007-01-16
> **EdThaSlayer said:**
> The first problem from my opinion is that they need to fix "fgrlx" properly so that it can compete with the Nvidia drivers(compare a Geforce 2 1000 fps against my 9600 that has 1500 fps, big difference in performance and BIG difference between the price of these two[fyi:I actually tested this]).There is a beryl benchmark plugin although that's not exactly a very good benchmark either...

---

### Post by pormogo on 2007-01-17
/sigh I just got finished moving and I apparently broke my fglrx 3d rendering while I was trying to get the open source driver working. Does anyone have a walkthrough on how to get the open source driver working? Or the fglx driver, I thought mine should be wokring based on.

[i]darthbator@pleasantodor:~$ dmesg|grep fglrx
[17179596.664000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179596.664000] [fglrx] Maximum main memory to use for locked dma buffers: 1414 MBytes.
[17179596.668000] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2006] on minor 0
darthbator@pleasantodor:~$ [/i]

could anyone happen to turn me in the right direction. BTW we're still a no go on aiglx support under the new fglrx?

---


---
title: "Hm... Some small things to take note of in Ubuntu 10.04"
date: 2010-05-01
forum: The Cafe
---

### Post by OmegaAI on 2010-05-01
I am just going to rattle off little things I have noticed so far between 9.10 and 10.04:

Obvious:
Changes under the hood
Better look
faster
easier installation (and here I was thinking it couldn't have become any easier)
multiple other things

Something you may have not noticed

If you install 10.04 32bit on a system with more than 3.5GB of ram, the kernel seems to be able to take advantage of it. I am using the full 4GB of ram on my system!!!!
Now I am not sure if the kernel was already precomplide to be set as PAE or if when I installed Lucid it  saw that I had 4GB of ram and enabled PAE


Just thought I would just mention so stuff.

~ OmegaAI

---

### Post by Lightstar on 2010-05-01
9.10 also had PAE install automatically.
I'm glad they did, no need to download server kernels anymore :)

I went on 64bit yesterday, had troubles that couldn't be fixed, now I'm back on 32bit.
Did the same thing for 9.10
Will see if I have to stay 32bit for 10.10 when that comes out.

---

### Post by OmegaAI on 2010-05-01
Hm... Thanks for point that out. tahnks

---

### Post by phrostbyte on 2010-05-01
Yes the 32-bit version of Ubuntu should support up to 64 GB of address space.

---

### Post by tgalati4 on 2010-05-02
That may explain why some people are having trouble with Lucid 32-bit on older hardware (where they were using Jaunty/Hardy before).  Some older hardware may not support PAE and that would definitely cause problems.

---

### Post by OmegaAI on 2010-05-02
Correct. My old T43 would crock on this... D: no 10.04 for it

---

### Post by WinterRain on 2010-05-02
> **OmegaAI said:**
> Correct. My old T43 would crock on this... D: no 10.04 for it

I use Lubuntu on my old thinkpad and it works fine.

---

### Post by earthpigg on 2010-05-02
> **phrostbyte said:**
> Yes the 32-bit version of Ubuntu should support up to 64 GB of address space.

sooo 6gb of ram would all be recognized oob?

---

### Post by OmegaAI on 2010-05-02
Obvious YEP

---

### Post by tgalati4 on 2010-05-02
There may be a kernel boot code to turn off PAE.  Then you could simply modify your GRUB entry and run Lucid without PAE.  That might work for older hardware.  Or somebody can take the time to respin the Lucid kernel without PAE.  Updates to the kernel would have to be performed manually from then on.

---

### Post by Dr. C on 2010-05-03
I run Ubuntu 10.04 on a Compaq EVO 1000c laptop the was "designed for Microsoft Windows 2000" with no problems. By the way 10.04 fixed two very annoying problems in 9.10:
1) The 3.5 in floppy drive did not work in 9.10 it works great in 10.04
2) The trackpad did not work for left handed use in 9.10 it also works great in 10.04

The specs are:
Pentium M 1.8GHZ processor
1 GB of RAM
ATI Mobility Radeon 7500 32 MB 1024 x 768
120 GB Hard Drive
DVD Reader / CD Burner
3.5in Floppy Drive 
Wireless N/G/B (Ralink RT RT2800)

---

### Post by OmegaAI on 2010-05-04
Hm.. I guess it all depends on the the BIOS and or mobo in your computer... I just installed 10.04 on my T43 and it runs great!

---

### Post by earthpigg on 2010-05-04
> **OmegaAI said:**
> 
> sooo 6gb of ram would all be recognized oob?
Obvious YEP

so... BIOS recognizes 6gb of Ram, ubuntu, however only sees 3gb.

```
[chris: ~]$ uname -a
Linux chris-desktop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
[chris: ~]$ f
             total       used       free     shared    buffers     cached
Mem:          3015       2870        145          0         41       1520
-/+ buffers/cache:       1308       1707 (playing with google earth atm)
Swap:            0          0          0
[chris: ~]$ 

```

dont want to make a whole support thread about it, but all i should theoretically have to do is install the linux-generic-pae package that will theoretically pull the latest pae kernel whenever the time comes? or would linux-image-2.6.32-__-generic-pae be more appropriate? linux-image-2.6.32-__-generic is what got installed.

---

### Post by migs73 on 2010-05-04
I would be interested to know how this works too. I have Lucid (upgrade from Karmic) but it does not use the PAE kernel. I have just upped from 3Gb to 4 but system monitor and $free -mt still only show 2.6Gb.
Is it only clean install that use the PAE kernel?
Is there some limitations in my hardware that has stopped the PAE kernal being installed? 
I would like to know before I try to change the kernel to the PAE version.
My BIOS also sees all 4Gb.

---

### Post by migs73 on 2010-05-04
A little update on what I said before.
Please see this;[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

Followed this and now I see 3.8Gb of my 4. Much more like it, and so simple.
Apparently if you already have 4Gb or more on a 32 bit machine 10.04 automatically uses the PAE kernel when you install (I didn't).

---

### Post by battlecyborg on 2010-05-05
I've run the distribution upgrade from 9.10 (and earlier) to 10.04LTS this past weekend.  I want to now use PAE kernel by default whenever auto-update kicks in to update kernels.  Is there a config file I need to set which default I'd like to use?  I was able to successfully install the pae kernel with aptitude and edit my grub file, but I'd like the pae kernel to be downloaded and installed automatically in the future.

Is there a way to do this?

---

### Post by earthpigg on 2010-05-06
> **battlecyborg said:**
> I've run the distribution upgrade from 9.10 (and earlier) to 10.04LTS this past weekend.  I want to now use PAE kernel by default whenever auto-update kicks in to update kernels.  Is there a config file I need to set which default I'd like to use?  I was able to successfully install the pae kernel with aptitude and edit my grub file, but I'd like the pae kernel to be downloaded and installed automatically in the future.

Is there a way to do this?

the linux-generic-pae and linux-headers-generic-pae packages pull the newest pae kernel every update -- im looking at the update screen now, and it has new pae kernels listed :P

---

### Post by Mr. Picklesworth on 2010-05-06
Still my favourite little thing: Volume indicator pulses red if sound is muted and something tries to play sound :)

---

### Post by migs73 on 2010-05-07
> **battlecyborg said:**
> I've run the distribution upgrade from 9.10 (and earlier) to 10.04LTS this past weekend.  I want to now use PAE kernel by default whenever auto-update kicks in to update kernels.  Is there a config file I need to set which default I'd like to use?  I was able to successfully install the pae kernel with aptitude and edit my grub file, but I'd like the pae kernel to be downloaded and installed automatically in the future.

Is there a way to do this?

I think this is now set as your default kernel and as such will be the one updated when required.

---

### Post by migs73 on 2010-05-08
> **earthpigg said:**
> so... BIOS recognizes 6gb of Ram, ubuntu, however only sees 3gb.

```
[chris: ~]$ uname -a
Linux chris-desktop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
[chris: ~]$ f
             total       used       free     shared    buffers     cached
Mem:          3015       2870        145          0         41       1520
-/+ buffers/cache:       1308       1707 (playing with google earth atm)
Swap:            0          0          0
[chris: ~]$ 

```

dont want to make a whole support thread about it, but all i should theoretically have to do is install the linux-generic-pae package that will theoretically pull the latest pae kernel whenever the time comes? or would linux-image-2.6.32-__-generic-pae be more appropriate? linux-image-2.6.32-__-generic is what got installed.

Earthpigg,
I take it you have tried the instructions on the link I posted?
Do you have 6Gb now? I have recently (after changing to PAE) read only newer processors (> 5 years??) have the NX bit capability to allow PAE. Don't know if the OS is clever enough to know if this is the case and disallow install of the PAE  kernel, or if it will just fall over after install? Luckily my processor allows it.

---

### Post by Swagman on 2010-05-08
Anyone thinking of getting an Asus M4A87TD Evo Mobo should be aware that the sound output is extremely muffled somewhat like turning the treble down to minus 5

Very disappointed.

Anyone know of an equaliser I can install ?

---

### Post by rhinert on 2010-05-23
> **Swagman said:**
> Anyone thinking of getting an Asus M4A87TD Evo Mobo should be aware that the sound output is extremely muffled somewhat like turning the treble down to minus 5

Very disappointed.

Anyone know of an equaliser I can install ?



I have not been able to get sound functioning at all on this motherboard.  Getting ready to load a copy of windows to see how it handles the built-in sound.

Seems like linux could use some good quality diagnostic tools for this kind of problem.  If you've looked at the sound diagnostic how-to, you know how primitive and scattered the process is.

---

### Post by lancest on 2010-05-23
I've had on board sound end up failing several times with Ubuntu as OS. 
I just count it as a hardware defect and install a sound card. 
If using Windows the defect may be masked.

---


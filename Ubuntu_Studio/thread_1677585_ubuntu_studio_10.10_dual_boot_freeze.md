---
title: "ubuntu studio 10.10 dual boot freeze"
date: 2011-01-28
forum: Ubuntu Studio
---

### Post by Quazimoto on 2011-01-28
EDIT: 

FireGL workstation video card issue! I had to remove the FireGL v7700 and use the built-in video to finish the install. I had ATI video built in so it was easy to then alow Ubunto to give me the proprietory driver needed for ATI 3D cards. Once done I shut down and put the FireGL back in. Worked great. in this process I learned not to get the driver from the AMD site as it messed everything up, but that may be my lack of experience.


OLD Message:

Hi!
I have a good install disc and it was tested on my other box.

I have installed it "successfully" next to windows 7on 640 gig drive. I have given 340 gig to ubuntu.

On boot using grub it freezes just after the mouse text in safe boot, about 2 to 3 lines down dealing with swap.

It freezes in both start-ups available that is how I found that it freezes at this point above.

I am using 4 core AMD phenom (black 3.4mhz), MA785GM gigabyte MB, dual monitors w/ATI firegl v7700 card, 6 gig 800mhz ddr2 ram. I do have 2 USB devices attached, one is a logitech wired mouse the other a wacom tablet... I am hard pressed to think either is at issue.

I am frustrated as I can not get in to check logs, etc... I think it is video related? But... no idea what steps to take. I can install a different distro, but this is my business that is dieing here so I do not want to spend a lot of time experimenting... 

Thanks for any and all help!

---

### Post by cchhrriiss121212 on 2011-01-29
If you cannot get past boot up, then you will have to reinstall. I take it Win7 is still working?

If you want stability, go with 10.04 or Debian stable.

---

### Post by Quazimoto on 2011-01-29
Been there, done that, used a second disc, etc. I am not new to this... I have used linux and bsd for 6 years now. yet, I am not the most experienced either as I am a designer not a programmer.

Yes, windows 7 worked, if it did not I would have looked into hardware issues... this distro worked on a similar machine from the same install earlier. I was under the impression 10.10 is the stable distro right now? I can go to 10.04, but I do have reasons to want the newer kernel and I am not really in the mood to use the 10.04 and mod that kernel since I know that this distro, "10.10" does work and is a good working distro since I did test it on a older box. I have a feeling there is a relatively easy fix once I get the run from cd version of ubuntu... I was hoping someone has run into a similar issue with the kind of hardware I am using?

Because of the work and applications I want to use for video I have to use 64 bit.

I am open for ideas. In the meantime, once I get the try-it-run-from-disc distro I am going to do a CD boot and run from there to look for any log that may help. The hardware is all good and tested with windows xp and 7 so far. XP is gone with the garbage it is... I would like to kill off all windows, but alas, I need to use certain 3D etc apps.

Thanks

---

### Post by cchhrriiss121212 on 2011-01-29
10.10 is stable but sometimes there are hardware regressions, and sometimes you will find a newer kernel does not play nice with certain hardware. The 6 month cycle is designed with the latest software in mind so stability is often compromised, 10.04 is an LTS and has been out for a while so it is a little more mature. You could always install a newer kernel on 10.04 so there is no need to mod anything:
[http://https://launchpad.net/~kernel-ppa/+archive/ppa]("http://https//launchpad.net/%7Ekernel-ppa/+archive/ppa")

> I was hoping someone has run into a similar issue with the kind of hardware I am using?
I think you are right that this is a video problem, ATI still lags behind Nvidia in support. And for that reason I don't think you will find many users with this specific card on here. Searching the forums/google does not bring up many results.

In my experience it is quicker to try another OS than it is to troubleshoot a broken install, especially if you have some sort of deadline to meet.

---

### Post by Quazimoto on 2011-01-29
There are deadlines and there are times when one needs to get back to work. I am at the third place; I do not want to spend days resolving this as I want to get back to what I do do sooner...

This distro was going to be my shortcut to a graphic design/video/music workstation.

Now I find that it is strange that my equipment is considered "old" and that an ATI firegl v7700, a high end workstation card for 3D work would not be covered by ubuntu studio. I can get linux based video drivers for this card... 
At least I know that this distro works great on an older box that uses a older X1300 ATI card and my v7700 is newer. Everything else I am using is from the last year or so...but not your average consumer setup for sure.

I can only figure that it is the openGL aspect of the v7700 card? Well, enough conjecture... I am going to do some testing once I am done setting up 3DS Max on the windows 7 side.

---

### Post by Quazimoto on 2011-01-31
Hi

Okay, here I have it. I can not boot Ubuntu... period. At least I can not boot from any 10.10 and 10.04 ubuntu try-it disc.

I am guessing there is a bug that is responsible. Since I have a video card built into the hard drive My next step is to use that for my install. but that would mean I have to remove my v7700, etc. Then I am not sure it will work as I need it too once I am Done.

---

### Post by Quazimoto on 2011-02-01
Tried fedora, same problem. I have contacted ATI since this card is supposed to work with linux.

I can get to my ubuntu studio install now, I got ext2 reader. Now I need to find out how to place the parts I need in the file system to get past the video lock-up. I may try to post in an area where I may get someone up on video.

---

### Post by Quazimoto on 2011-02-01
So, I am just going to keep going until I find a 64 bit system that will work, But I do like the E17 desktop,  too bad it doesn't come in 64 bit...

But for me the good news is that if I look long enough and burn enough cd's I should find a distro. That is a waste though... I would much prefer to know what and how to mod this ubuntu studio install.

Solved using method I list in the first message above. I was not able to install any linux distro I tried, even those that did boot from a CD or DVD. I did not try them all, for obvious reasons.

---

### Post by jeremyjjbrown on 2011-04-14
The real problem here is that Ubuntu amd64 10.04 and 10.10 will not boot in vesa mode (safe video). The ubuntu dev team spends way to much time playing with fonts, trying to make orange and purple match (they don't and never will), moving buttons around, building yet another window manager for linux that no one needs or wants, and taking away basic functionality like java jre/jdk, aptitude and synaptic. If they just made sure basic things worked properly Ubuntu would have twice as many users. How can they allow vesa mode to fall through the cracks for two releases?

---

### Post by drjzzz on 2011-10-02
My dual-boot works fine with Windows but hangs with Ubuntu.  Watching the boot process, Ubuntu hangs on the CD/DVD player (Sony, legacy interface (not SATA)).  When I inactivated that interface, it boots fine.  Not an ideal solution!

---


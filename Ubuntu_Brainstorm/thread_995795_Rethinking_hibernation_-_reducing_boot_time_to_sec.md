---
title: "Rethinking hibernation - reducing boot time to seconds"
date: 2008-11-28
forum: Ubuntu Brainstorm
---

### Post by Devport on 2008-11-28
**[COLOR="Red"]Edit : It turned out that there is a showstopper : the filesystem state.[/COLOR]**

*_Today there are two major ways to start a system_* :

 *Normal boot including full system initialisation*
- the main advantage is that the resulting system is clean
- the main disadvantage is that it takes way to long ( I want my system to be instant on )

 *Hibernation aka suspend to disk*
- the main advantage is that it is incredibly fast
- the main disadvantage is that it is not clean - it couldnt replace a normal system startup completly since it would bork the system after some time

 *_I propose a new boot mode_*
Unlike hibernation there will be a **persistant** resume image of the system at a certain stage ( e.g. the gdm login screen ). Whenever the system is booted this image will be loaded so that boot time will be as fast as it would be using hibernation, but due to the fact that it is a persistant image it wont suffer over time and the system will always be as clean as if it was booted normally.

I think we have to rethink. For now its a hack - but in truth the way its done today is wrong. A computer system almost never changes ( hardware ) - so why is it detected, intialised, and loaded file by file every time. Maybe doing this only when the system ( hardware / system software ) really changes is the way to go. Maybe in the future the kernel willl have modules which are detected / started / initialised individually to adjust the boot image to the current system state out of a running system or on demand and not the whole system check again and again for no reason.

*_For this to work it will have to be integrated into the system_*
- If there is no image a new clean one has to be created
( when the respictive stage is reached, e.g. gdm is fully loaded )
- If the system changes a new clean system image has to be created
( after next reboot )
- On demand a "normal" hibernation + resume can be performed
( a current, non persistant hibernation image will be loaded if available )
- On demand a "normal" boot proccess can be performed.

I hope you get the point of this idea.

Notes :
- I think of this new startup mechanism as the standard way of booting a system - at least for those who want it.
- For a quick proof of concept I will try to implement it in a minimalistic form using current hibernation tools soon
- I posted this to gentoo forums as well

---

### Post by regala on 2008-11-28
> **Devport said:**
> *_Today there are two major ways to start a system_* :

 *Normal boot including full system initialisation*
- the main advantage is that the resulting system is clean
- the main disadvantage is that it takes way to long ( I want my system to be instant on )

 *Hibernation aka suspend to disk*
- the main advantage is that it is incredibly fast
- the main disadvantage is that it is not clean - it couldnt replace a normal system startup completly since it would bork the system after some time



What do you mean by "it would bork the system after some time" ?
looks like a false claim to me. A system waken up after suspend2disk is as rock solid as with a "normal" boot, at least here.

> 
 *_I propose a new boot mode_*
Unlike hibernation there will be a **persistant** resume image of the system at a certain stage ( e.g. the gdm login screen ). Whenever the system is booted this image will be loaded so that boot time will be as fast as it would be using hibernation, but due to the fact that it is a persistant image it wont suffer over time and the system will always be as clean as if it was booted normally.


Well, it's not as simple as that. You did not take account of the a simple fact: a resume image is time,date,filesystem,currently-running-processes,dependent. I.e. when you go to resume and then back to "life", in the meantime, your filesystem is not broken, but in a state that depends directly from the image. And if, by "chance", you were to boot a resume image on a clean filesystem, you may certainly completely break the root filesystem to the point fsck may not be able to repair it.
The idea is fine, real fine, but it just won't work.

-- 
Mathieu

---

### Post by regala on 2008-11-28
To put it clearly, if you boot a system with a resume image that was not built during the last suspend operation, and if the system has run _after_ you built the resume image, in any way, you're doomed. A resume image is of no use if the system ran after its creation.

-- 
Mathieu

---

### Post by smartboyathome on 2008-11-28
I was thinking about this idea for a while, and while I think it may be good for the future, I think the direction to go is to speed up the boot process, not use psuedo speed ups. This wouldn't work in a couple cases:

1) The hardware doesn't have hibernation support or hibernation support for the hardware is broken. This could cause the computer to then turn on with disastorous results. On Arch Linux, you have to play around with hibernation and suspension to see if it even works, changing settings and such and hoping you don't have to do too much to get it to work.

2) Your computer crashes. My computer crashes sometimes (usually my fault because it overheats, but I'm hibernating it now so that I can avoid this), but this would mean that bootup time would be all but abandoned because not as many people would see it. With bootup times abandoned booting up after a crash could be even worse than now.

---

### Post by Devport on 2008-11-28
> **regala said:**
> What do you mean by "it would bork the system after some time" ?
looks like a false claim to me. A system waken up after suspend2disk is as rock solid as with a "normal" boot, at least here.
After some time means when you do it often memory gets filled because there are always apps which leak it. If you would hibernate / resume only without ever restarting the system there will be a slow down to a crawl due to swapping and even worse impacts will happen.

> **smartboyathome said:**
> 1) The hardware doesn't have hibernation support or hibernation support for the hardware is broken. This could cause the computer to then turn on with disastorous results. On Arch Linux, you have to play around with hibernation and suspension to see if it even works, changing settings and such and hoping you don't have to do too much to get it to work.
Its obvious that on such system the normal bootup would be used.

> **smartboyathome said:**
> 2) Your computer crashes. My computer crashes sometimes (usually my fault because it overheats, but I'm hibernating it now so that I can avoid this), but this would mean that bootup time would be all but abandoned because not as many people would see it. With bootup times abandoned booting up after a crash could be even worse than now.
This may be solved by doing a normal boot after a crash until the system is sane again.

---

### Post by Devport on 2008-11-28
Any ideas to solve the file system dilemma are welcome !

---

### Post by regala on 2008-12-09
> **Devport said:**
> Any ideas to solve the file system dilemma are welcome !

You do not understand that it is unsolvable; when you put your box to sleep to disk, the root file system is never closed, because the kernel is still using it. There is no way the root file system can be closed and left in a consistent state _unless_ you umount it, i.e. you shutdown the system...

The state you want to restore is a state with "heavy" and several references hanging on the root file system. Your idea would be interesting to boot a livecd or a system with a readonly root filesystem. And any filesystem opened for writing and you have actually written to would have to be closed before "suspending". The real problem is that across reboots, with your system filesystems would have to stay _exactly_ the same, no change at all on disk.

---


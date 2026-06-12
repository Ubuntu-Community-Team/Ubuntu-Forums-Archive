---
title: "vbox xp guest slow system clock"
date: 2010-01-13
forum: Virtualisation
---

### Post by estyles on 2010-01-13
Running an XP guest in a virtualbox, the machine worked fine until yesterday, when all of a sudden, the guest's system clock is REALLY slow.  It's about 1/7th the speed it should be, and therefore the guest's clock falls behind very quickly.  It loses about 6 minutes every 7 minutes.  This puts it out of sync with active directory and means that I can't access domain resources from the VM.

Also, it slows down GUI animations such that it feels like the machine is unresponsive, but there's no corresponding slowdown on processing or typing or anything that doesn't involve an animation as far as I can tell.

The second symptom would be reasonably easy to fix - just set the delay for menus and stuff to 0.  But the first symptom is more difficult and more important.

I'm not sure what version of VBox I was running yesterday - probably 3.0.4.  Or whatever was most current up until the latest upgrade.  After I started having the problem, I uninstalled virtualbox and installed 3.1.2.  The guest OS is Windows XP SP3.

Anyone have this problem or have a fix?

---

### Post by SecretCode on 2010-01-14
I suggest you take this problem to [http://forums.virtualbox.org/](http://forums.virtualbox.org/) - lots of information and experts there.

---

### Post by estyles on 2010-01-14
Thanks.  That was actually helpful.

Found [this topic]("http://forums.virtualbox.org/viewtopic.php?f=7&t=23978"), and specifically this: 

> I was having this issue with Kubuntu Karmic 64 bit host and Windows XP 32 bit guest. I switch to realtime kernel and works awesome. Steps:
1. Install linux-image-rt
2. Install linux-headers-rt
3. Make sure it is set as the default kernel. I did it by checking the grub init screen, and settings its index in /etc/default/grub (GRUN_DEFAULT)

Hopes this helps anyone else, and thanks to qhartman for the tip.

Which I tried, and it seems to be helping.  The clock is still a little wonky, but now it seems to vary between 90% and 110% of the speed it should be, and VBox corrects the time if it drifts off by too much.  So much better than 1 second for every 6-10 seconds of real time like it was.

Two notes for anyone having the same problem and wanting to try the realtime kernel:
1) As of now, the latest rt kernel is 2.6.31-9-rt (don't install it directly, just install linux-image-rt and linux-headers-rt), which is a few numbers off the latest generic kernel.  Although it's still 2.6.31, so it shouldn't lack any major features or security patches.

2) To set it as the default (in Karmic anyway), the easiest way is to go to System->Administration->Startup Manager, and choose default OS to be the one with the "rt" in the kernel name.

---


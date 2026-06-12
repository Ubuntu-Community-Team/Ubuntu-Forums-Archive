---
title: "Strange behavior in server"
date: 2011-10-25
forum: Server Platforms
---

### Post by Jarozas on 2011-10-25
Hello,
 
I'm running a 11.10 with the mail system fixed like described in other post.
 
Sometimes the system froze without any apparent reason and clicking briefly the start button (phisically), without restart the machine, returns it to life.
 
During this "freeze state", you can ping from server to other computers, but no from other computers to the server.
 
I've read some irregular behaviors in servers after software automatic updates like clamav, etc... Don't know if it is the cause.
 
Anyone have see something like that?
 
Thanks.

---

### Post by Demented ZA on 2011-10-25
> **Jarozas said:**
> Hello,
 
During this "freeze state", you can ping from server to other computers, but no from other computers to the server.
 
Thanks.

I assume that the server can't be in a frozen state when you are doing a ping from it, since you have to interact with it, and thus the machine will be brought to life.

Sounds like the machine is being "paused", and unable to process. Could it be a power saving feature? Check your BIOS for any power features/CPU throttling etc and turn them off. Even if its not a setting in the bios, Ubuntu could be recognizing a hardware feature, and not correctly using it.

Out of curiosity, what Motherboard are you running? Also, what HDD's you running? Anything "Green"?

---

### Post by Jarozas on 2011-10-26
Hi Demented,
 
Thanks for your answer. 
I can realize this is a hardware fault. But what is really strange is that server can work fine for weeks and suddenly this apears again.
I'm currently planning to move the server install to a new PC box and install some LTS distribution, I've enough strong emotions with normal releases and upgrades and updates.
 
I supose is unrelated, but the server clock is running slowly, loosing several minutes for day.
 
By the way, is "green" a brand name?

---

### Post by Demented ZA on 2011-10-26
Green is not a brand name, its more a sales slur. Green refers to environmental impact, such as power savings. An example would be Western Digital and Seagate's Green drives: unlike conventional drives that stick to 5400rpm or 7200rpm etc, they idle at ~5900rpm, and spin up to 7200rpm under load. This allows them to save power and prolongs the lifespan of the drive, they are also somewhat cheaper, however, these seem to be problematic, at least in RAID arrays because the drives lose sync due to the power savings implemented by each drive, and not the RAID Controller/Software. Motherboards with this functionality can down-clock/underclock the CPU for instance, similar to intel's speedstep technology. 

If these functions are used incorectly, you can have freezes (until you interact with the machine), as well as loss or gain (unlikely) of time.

I don't think LTS or short term releases is really the problem though. I rather think problems occur as a result of an upgrade. Somehow, Ubuntu seems to fill every crack and crevice of a machine when installed from scratch, wheras upgrading to the same release seems as if there is no awareness of your hardware and software configuration.

Re-installing will probably resolve it, although it would be nice to  know what the root cause is. One can't always re-install when faced with  a production server.

Please post back here and let us know what you find though :-)

---

### Post by Jarozas on 2011-10-26
Hi Demented,
 
Using the lshw command, I've find that my motherboard is an ASUS A7V400-MX, and the processor is an AMD Sempron 2800+.
Is this giving you some clue?
 
There's any software like Everest suitable for Linux? 
 
Thanks.

---

### Post by collisionystm on 2011-10-26
> **Jarozas said:**
> Hello,
 
I'm running a 11.10 with the mail system fixed like described in other post.
 
Sometimes the system froze without any apparent reason and clicking briefly the start button (phisically), without restart the machine, returns it to life.
 
During this "freeze state", you can ping from server to other computers, but no from other computers to the server.
 
I've read some irregular behaviors in servers after software automatic updates like clamav, etc... Don't know if it is the cause.
 
Anyone have see something like that?
 
Thanks.


It could be software related.

Go with something stable for a server such as 10.04 LTS or Debian Squeeze.

---

### Post by Demented ZA on 2011-10-27
> **Jarozas said:**
> Hi Demented,
 
Using the lshw command, I've find that my motherboard is an ASUS A7V400-MX, and the processor is an AMD Sempron 2800+.
Is this giving you some clue?
 
There's any software like Everest suitable for Linux? 
 
Thanks.

Wow, that takes me back to the days of Pentium4's! Oh wait, I think I have one that still works around here somewhere.

Well since "Green" functionality is a recent development, it rules that out. So were basically back to square one. Considering the age of the hardware, its entirely possible that something has started going wrong. Hardware is in a constant state of degradation. It will fail eventually. The question isn't if, but when. The easiest way to rule it out though, or to establish if its a software related problem is to do a fresh install. 

At this point I agree going for an LTS release. You need to rule out as many problems as you can first, and since the x.10 releases of Ubuntu are closer to bleeding edge, they can have problems.

I'd say backup (you have a VM, so I'd say you are covered), re-install, and see what it does. You can always copy your scripts and configs etc. back when you are done.

Given that you are looking at a new system, I suppose there will be little incentive for you to do it on the old system. At least, if you upgrade, use the old system for playing around and see if you can solve the problem. 

I'd very much like to know what the problem is.

---

### Post by Jarozas on 2011-10-27
Hello.
 
I've used frequently old hardware to install my servers. 
Now I'm installing a 10.04 LTS over an Athlon 700 MHz with 640 MB RAM and 40 GB HD, with no problem. I believe this capability of low hardware requirements is a fundamental reason for to use Linux instead of Windows servers.
 
I'm considering now moving to 10.04 LTS all my servers.
 
When you run a LTS version, are all the updates safe? 
Should you test any new update before apply to a production server, even if you run a LTS?
 
I've used without any significant problem Red Hat (long time ago), briefly Fedora and Ubuntu for my servers. But now I'm facing problems that sound like is time to move again... maybe to Debian that could be more familiar than other distro.
 
Thanks.

---


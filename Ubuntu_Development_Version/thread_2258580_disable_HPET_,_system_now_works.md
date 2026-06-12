---
title: "disable HPET , system now works"
date: 2014-12-28
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-12-28
I was testing Lubuntu (and other) isos on this one AMD64 bit machine and the USB boot isos would just not boot up. On Lubuntu it booted once, started a hard install and then failed. I was just ready to bin this machine and decided to try and disable HPET (High Precision Event Timer ) and , voila', I have this machine back working again.

---

### Post by Hazzabin on 2014-12-28
Great one mate, 

can you tell how you did this if the machine didn't couldn't boot, 

I have an old machine that gave me grief I do not know if the issues were the same as you had

---

### Post by ventrical on 2014-12-28
> **Hazzabin said:**
> Great one mate, 

can you tell how you did this if the machine didn't couldn't boot, 

I have an old machine that gave me grief I do not know if the issues were the same as you had

It would boot from some SATA drives I had installed - but then became unstable. The machine booted into BIOS but would not boot USB flash drives. I was using this as a swapper desktop. Go into you BIOS and look for  HPET. I have 3 machines and they are all in different spots, Advanced , OnBoard Configuation .. etc.. If you find it , disable it then USBs will boot.

*note*

Having HPET enabled will give the impression that something is wrong with hard drive, power supply or processor. I read up on it and it says that linux had fixed this since 2.6.x-x kernel ??

Hope that helped . If not lemme know.

Regards..

*now off to do a Lubuntu altenate install on an EasyPeasy netbook .. :) lol

---

### Post by Hazzabin on 2014-12-29
"[COLOR=#000000]install on an EasyPeasy netbook ." well sure hopes it was easy lol

Thanks mate for the info will give it a try my tomorrow[/COLOR]

---

### Post by kostkon on 2014-12-29
[3.18 mystery bug that might be related to HPET]("http://www.phoronix.com/scan.php?page=news_item&px=MTg3Mzk").

---

### Post by ventrical on 2014-12-29
> **kostkon said:**
> [3.18 mystery bug that might be related to HPET]("http://www.phoronix.com/scan.php?page=news_item&px=MTg3Mzk").

Thanks.

> 
The latest belief is [the issue might be related to HPET]("http://lkml.iu.edu/hypermail/linux/kernel/1412.3/00684.html"), the High Precision Event Timer. Yesterday [Linus Torvalds posted]("http://lkml.iu.edu/hypermail/linux/kernel/1412.3/00703.html")  that he agrees it could be HPET related and the cause would likely come  down to an actual hardware bug, some SMM/BIOS power management feature  causing the problem, a bug in the kernel's clock-source handling, or  "gremlins" -- something freakish happening. In [a follow up response]("http://lkml.iu.edu/hypermail/linux/kernel/1412.3/00707.html"),  Dave Jones is starting to think it could be due to some BIOS /  motherboard error with the Intel server motherboard he's been using  given there was a sort of similar bug report from last year. The issue  for Dave though only started recently with the kernel, but if it looks  to be a hardware issue, [the HPET problem wouldn't be investigated further]("http://lkml.iu.edu/hypermail/linux/kernel/1412.3/00737.html"). 


 Actually it is very capricious. On some of my earlier vivid ubuntu installs  it will declare the BIOS BUG in verbose script before startup. Just never thought much about it. But I'm using 3.16.x-28 kernel so if this is the case it has rolled back  all the way there (and also to 14.04.1 lts set.) so it looks to be more serious.

On one of my HPET enabled machines I first:

Changed the memory.
Changed the power supply.
Changed the video adapter.

None of this resolved the problem. Disabled HPET resolves. This is a clankswerks in the classic sense. (Hey Linus .. guess what ..a real clankswerks!  member those olde days:) )

Regards..

---

### Post by ventrical on 2014-12-29
HPET is found in:

BIOS/Power/APM Configuration/HPET Support = disabled (should be for fix)

Regards..

This was specifically designed to  "Increase the performance of Vista Multimedia Player. Hardware High precision efficient timer can meet Vista's requirement. Suggest to disable this feature if OS in running below XP."

---


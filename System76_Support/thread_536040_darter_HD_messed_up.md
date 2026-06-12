---
title: "darter HD messed up?"
date: 2007-08-27
forum: System76 Support
---

### Post by Rotarychainsaw on 2007-08-27
OK, I have a older darter, the white kind...
Everything has been working great. Now this morning, I woke it up from suspend, and it wasn't really working right. I tried to restart and it wouldn't so I just held the power button until it shut off. 

When I rebooted, it says to put in valid boot media or something like that, and then drops me into a little grub shell. I popped in the ubuntu live cd, and gparted says that the whole drive is unallocated. 

Its really weird because I haven't updated the kernel or messed with grub in a long time, maybe the hard drive's FAT got messed up somehow. Anyone have any suggestions? Thanks.

---

### Post by thomasaaron on 2007-08-27
Try pressing escape when it gets to the intel splash screen.
Does it give you an option to boot from the HD? And if you try to do that, what happens?

---

### Post by Rotarychainsaw on 2007-08-27
ok, back from class and ready to troubleshoot!

pressing escape and booting from the hd had the same effect of getting the grub shell to come up. From what I can tell, the partitions are intact, but the format isn't being recognized as ext3 anymore (ext2?).

---

### Post by Rotarychainsaw on 2007-08-27
Oops, just made it worse with testdisk haha. I think I erased the MBR. Gparted was still telling me bad superblock and stuff like that. Oh well, I'm gonna put gutsy on it, that should let me know if the HD is buggered or not.

---

### Post by Rotarychainsaw on 2007-08-27
Is that piix kernel bug still in gutsy? Where the HD would time out? Cause I was getting an error that said I/O refused to dead device, but gutsy did install and run for a little bit.

---

### Post by thomasaaron on 2007-08-28
So far, Carl is the only one who upgraded his DarU1  (white) to Gutsy. If I remember correctly, the problem *did* exist in Gutsy, but I'm not completely sure.

Also, it is a little difficult to test at this point, as we've all applied the firmware update to our Darters to completely fix the problem.

If you have not done so yet, the fix is here:
[https://bugs.launchpad.net/system76/+bug/117441](https://bugs.launchpad.net/system76/+bug/117441)

---

### Post by Rotarychainsaw on 2007-08-28
Hmm, I've never seen that... I guess I gotta go borrow some usb drives and try it out. May as well update the bios too and get those brightness keys working lol. Thanks.

I guess I should start complaining about whatever corrupted my drive too though, I think it may have been because I always use suspend instead of shutdown... Boo!  haha

---

### Post by Rotarychainsaw on 2007-08-28
IT DID IT AGAIN! Dang, I was hoping it was a one time accident, but I think the hard drive is dying or dead. 

A 2 day old gutsy install, just tryed to start it up and got grub error 16 which indicates a messed up filesystem. I tryed to hit escape to get the boot menu, but only the cd drive was listed. The HD was detected in the BIOS though.... Anyway, any ideas or should I contact system76 hardware dept.

edit - and 5 minutes later it boots up again....  Well, random failing like that usually indicates hardware, right?
more edit - after 30 seconds, get rejecting I/O to dead device.
more edit - took the drive out and put it back in again. Seems to be working so far. we'll see...

---

### Post by thomasaaron on 2007-08-29
Hopefully, reseating it will be the fix.
If not, call me at support.

---

### Post by Rotarychainsaw on 2007-08-29
so far so good. I'm keeping my fingers crossed.

---

### Post by beuno on 2007-08-30
> **thomasaaron said:**
> So far, Carl is the only one who upgraded his DarU1  (white) to Gutsy. If I remember correctly, the problem *did* exist in Gutsy, but I'm not completely sure.

I've just installed a fresh Gutsy Tribe5 on a new partition in my daru1 and everything worked perfectly. I haven't even applied the System76 Driver.
I only tested real quick the wireless, and compiz was working great by default. 

I'll open up a thread about it as soon as a spend a few days on it  :D

---


---
title: "Good or bad idea:  FSCK done at shutdown, instead of startup"
date: 2009-04-01
forum: The Cafe
---

### Post by diablo75 on 2009-04-01
I hate sitting through file system checks every 30th boot, and hitting escape just postpones it one more boot; you have to do it eventually.  What if, instead of postponing it to the next boot, it's just postponed to the current sessions shutdown sequence?  It'd take place even sooner than it would if you hit escape, and you can just walk away from your PC to let it do the check and not have anything to wait on.  In the interest of making something like this eco-friendly, the PC would proceed to shutdown, even in the event of finding an error, presenting any error messages on screen upon next reboot.

Good idea?

---

### Post by MaxIBoy on 2009-04-01
FSCK is usually only needed if the previous shutdown wasn't a clean one, and if there actually are any errors, it's advisable to perform the scan before you write anything to the filesystem. So if you hard-reset or something, the scan would get skipped until you shut down, by which time you might have tried to save something to the filesystem and made the problem worse.

---

### Post by SunnyRabbiera on 2009-04-01
Maybe, but I can see how it could cause issues.
Its easier to scan filesystems when the kernel is starting up then shutting down, also I find it easier to get out of a fsck in linux then on windows.

---

### Post by cariboo on 2009-04-01
Now that ext4 is available, a fsck of my 250Gb drive takes less than 10 seconds. My normal boot time is 21-22 seconds, fsck ran this morning and the boot time went up to 29 seconds. It was done before I got back with my cup of coffee.

Jim

---

### Post by t0p on 2009-04-01
Personally, I like the idea of the test being done on shutdown instead of boot.  But I have no idea what the technical realities of such a change might be.

---

### Post by calrogman on 2009-04-02
> **cariboo907 said:**
> Now that ext4 is available, a fsck of my 250Gb drive takes less than 10 seconds. My normal boot time is 21-22 seconds, fsck ran this morning and the boot time went up to 29 seconds. It was done before I got back with my cup of coffee.

Jim

I see you like the boot-speed of 9.04a?  It is rather impressive, but how did they do it?  Does anyone here know?

---

### Post by diablo75 on 2009-04-02
Well I'm not going to just be able to convert over to ext4 from ext3 can I?  Won't I have to wipe my install and start fresh?

---

### Post by ghindo on 2009-04-02
Well, your options are:[LIST]
[*]Run fsck manually, at your own leisure.
[*]Run ext4.
[LIST]
[*]Yes, you can convert ext3 to ext4.
[*]However, ext4 is still a bit unstable, so I would recommend waiting on that.
[/LIST]
[*]Cancel the fsck by hitting ESC.
[/LIST]

---

### Post by Skripka on 2009-04-02
> **ghindo said:**
> 
[*]However, ext4 is still a bit unstable, so I would recommend waiting on that.

[/LIST]

It isn't a problem with Ext4 so much as it is with apps that are not written with delayed allocation in mind.

---

### Post by gnomeuser on 2009-04-02
The basic intent is good, the implementation however is wrong. You assume you need the delay, putting it before or after doesn't matter. Look at the problem differently, how can we avoid having a mandatory pre or post mount fsck to ensure data consistency.

The answer is two-fold.

1) Implement online fsck, FreeBSD has had this since FBSD 5.0. You can fsck a mounted partition on a running system. The delay becomes background time during runtime.

2) Implement additional data safety and early warning systems. DeviceKit-disks is going to do this for us, letting SMART and other means of monitoring warn us of problems before they hit and adapt to fault scenerios.

That is a lot more work, but it is one solution that would solve the problem at hand and many other.

---


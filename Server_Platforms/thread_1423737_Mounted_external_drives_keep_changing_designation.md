---
title: "Mounted external drives keep changing designation"
date: 2010-03-07
forum: Server Platforms
---

### Post by Donny Bahama on 2010-03-07
I have a headless 8.04 server with 2 USB drives attached. I'm trying to move everything off the 1.5TB drive onto a few 300GB drives (so I can then use LVM on the 1.5TB drive and move everything back onto LVs.)

I check the drives using 'fdisk -l'. They show up as sdc1 and sdd1. I mount them and start a cp operation. After a long wait, I get a bunch of error messages like:
```
cp: cannot stat `Backup/Donny/website.zip': Input/output error
```When I run fdisk again, the drives are no longer sdc1 and sdd1. Now they are sde1 and sdf1 (and of course, they are no longer mounted.

What could be causing this and how do I fix it?

I need to fix this ASAP because the 1.5 TB drive seems to be going bad. Every few seconds I hear a big "click" as though the head arms are smacking against a stop. (This is the 2nd brand new 1.5TB drive that has started doing this!)

---

### Post by Donny Bahama on 2010-03-07
UPDATE

I unmounted and physically disconnected both drives, rebooted the server, reconnected and remounted the drives. The rsync operation seems to be running perfectly. Would still love to know what I might have done wrong the first time... or if this is typical of external drives attached to a server.

---

### Post by CharlesA on 2010-03-07
The "Input/output error" usually means that the drive is going bad. As for it switching designation, I am not sure why it would be doing that. I know mine switch sometimes (usually when I add another external drive, but for the most part they stay the same), but since I use the UUID to mount the drives that isn't a problem.

---

### Post by Donny Bahama on 2010-03-07
> **CharlesA said:**
> The "Input/output error" usually means that the drive is going bad.I'm pretty sure they gave that error just because they had unmounted themselves (and switched designations.) No way to write a file when the mount point is gone.> As for it switching designation, I am not sure why it would be doing that. I know mine switch sometimes (usually when I add another external drive, but for the most part they stay the same), but since I use the UUID to mount the drives that isn't a problem.Didn't know you could do that. I'll have to look into that. I assume that's in the man page?

Thanks very much for the response!

---

### Post by CharlesA on 2010-03-08
I am not sure if it's in the man page or not, but the syntax to mount it by UUID is:

mount -t ext3 UUID=uuid-goes-here /mountpoint/goes/here

Basically you are just using the UUID instead of /dev/sdxx

---

### Post by spynappels on 2010-03-08
That is very useful, thanks!

---


---
title: "mdadm issue, now allowing me to remove bad drive"
date: 2008-08-31
forum: Server Platforms
---

### Post by goldenfri on 2008-08-31
I have an issue with mdadm on Ubuntu server 8.04 (mdadm v2.6.3)

I am running a RAID 5 with 5 drives and a hot spare
One of my drives got a ton of bad blocks recently, so I marked it as failed and it automatically failed over to the spare and started rebuilding. So far so good.

When it finished I removed the bad drive in mdadm and everything is fine. 

So my issue is when I try and physically remove the bad drive from the system. When I remove any drive from the system it hangs at the raid part of the boot and won't boot.

Any ideas? I can leave the bad drive in and it works fine but I don't really want to do that.

---

### Post by tamoneya on 2008-08-31
this is just a guess but what is most likely happening is that mdadm is using the device names not UUIDs.  (Can you give UUIDs to mdadm It would make sense if you could but I have never done it).  Therefore if your drives are /dev/sda-f (a-e active with f as hot spare) and lets say /dev/sdb fails you rebuild on f.  However when you remove sdb things get renamed so that c = b, d = c, e = d, f = e.  This is a total shot in the dark but it is at least something to take a look into.  Chances are you will want to look into mdadm.conf and see if you can make some changes there.

---

### Post by fjgaude on 2008-09-01
Well, I've been through these things before... first using **mdadm** **fail** the bad drive, then again using mdadm **remove** it. That way **md** in the kernel knows what is what.

Software raid uses the superblocks mdadm places on each drive to know what is part of an array.

You might zero the superblock of the failed drive before you physically remove it.

---


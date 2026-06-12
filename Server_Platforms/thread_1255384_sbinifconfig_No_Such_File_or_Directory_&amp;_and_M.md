---
title: "/sbin/ifconfig: No Such File or Directory &amp; and Many More"
date: 2009-09-01
forum: Server Platforms
---

### Post by chrislynch8 on 2009-09-01
Hi,

I am getting a lot of errors on my 6.06 Server. My Networking is not working because I get the error in the Title.

Some programs in /sbin/ work and others do not.

for example ifonfig and ls do not work.
cfdisk, fsck do work.

How can I get these programs working again?

Rgds
Chris

---

### Post by chrislynch8 on 2009-09-02
Hi,

Just an update I managed to get the system booting again, the only issue is now that some of the Files in /bin and /sbin are the incorrect size. I can see this when I compare them to a backup I took last week.

How can I copy in the correct files to bin and sbin from my backup.

I tried to boot into recovery mode but I was not allowed to overwrite the ifconfig file in /sbin or the ls in /bin

I tried to boot in using the Ubuntu 6.06CD and chose recover a broken system but that wouldn't let me overwrite the files either.

I then tried to boot into Knoppix to mount the drives and copy them in that way but, I have software raid1 set up so even though I can see the partitions I need to access with fdisk -l, when I try to mount them I get "Unknown filesystem type 'mdraid'

What do I need to do to access my partitions via a live CD. do I have to create a raid1 on the live CD I found somje instructions to this but was unsure if it coulde damage my filesystem.

Rgds
Chris

---


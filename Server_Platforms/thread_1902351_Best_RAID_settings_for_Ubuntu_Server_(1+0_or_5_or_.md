---
title: "Best RAID settings for Ubuntu Server? (1+0 or 5 or NAS)"
date: 2011-12-30
forum: Server Platforms
---

### Post by Marcus Aurelius on 2011-12-30
I am installing a Ubuntu Server on a:

HP Proliant DL380 G4
Dual CPU's 3.20 ghz / 800 mhz / 1MB L2
5120 MB RAM
6 hard disks on HP Smart Array 6i controller (36.4 GB Ultra320 SCSI HD each)


I will be using this server to capture VHS video, encode, compress, cut, edit, make DVD's, rip DVD's, re-encode some more, generally convert large uncompressed files as routine.

I have options:

#1)  RAID set to RAID 5 (5 discs) with one spare (6th disk)
I liked this option, because of the spare.  My disks are getting older, then are going to brake down, and I really need redundancy.  However, I thought the parity processing would really slow down the encoding process.  !!!

#2)  RAID 1+0
I thought this would be faster, but I can either do 4 disks mirrored (leaves me really two disks size of 36.4GB x2)... Then I would have 1 spare, and one SCSI disk not being used sitting in the server.  (some what of a waste, unless I need a quick replacement).

With RAID 5 I have 5 disks @ 36.4GB each and 1 spare
OR
With RAID 1+0 I have 2 disks @ 36.4GB each but I have two spares and mirroring.

I am also considering purchasing a NAS.

Given these scenarios (RAID 5...RAID 1+0....either 5 or 1+0 using a NAS)

What is the best configuration for my needs?
Thank you.

---

### Post by rubylaser on 2011-12-30
It really depends on how important maximizing hard drive space is to you.  If it's not the upmost importance, a RAID10 does not have to do parity calculations and has the potential to be much more fault tolerant than a RAID5 array.  If you need maximum space, then RAID5 is for you.

---

### Post by kevinthecomputerguy on 2011-12-31
+1 Rubylaser, rock solid advice as always.

And then, the most important statement ever... treat your raid as if it wasn't raided. Back it up the same way you would a 15 year old, cracked, warped, water soaked floppy disk with hair on it. A good backup scheme is the only answer. (backup destination = offsite raid6 if possible, a network "backup" shouldn't need much speed performance)

My experience = Raid it and back it up as if it wasn't, and only go raid 10 if you get errors about disk performance. I only saw once where i needed raid 10, it was an inventory server with a huge database. With raid 5 \ 6 i did see performance errors. Raid 10 fix it. But except for that one scenario, i like raid 5 o.s. (/boot on a flash drive) and raid 6 data, both with awesome backup plans.

*I use a dd script in start-up to backup /boot to the data array

-Kev

---

### Post by spynappels on 2011-12-31
I don't know what your budget is, but I would have a combination of all the above. RAID1+0 on the server with 2 hot spares, and backed up to a NAS with RAID5 or 6. Also only store current/recent encoding jobs on the server and everything else on the NAS.

---


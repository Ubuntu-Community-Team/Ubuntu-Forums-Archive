---
title: "SCSI problems with IBM Xseries232"
date: 2009-04-22
forum: Server Platforms
---

### Post by Stuggi on 2009-04-22
I'm trying to install Ubuntu Server 8.10 on an IBM xseries232 that has a previous installation of Windows Server 2003

The HDD's are configured as follows;

ID0 8GB Array A (RAID 1)
ID1 17GB Array A
ID2 17GB Array B
ID3 17GB Array D
ID4 147GB Array C (RAID 0)
ID5 147GB Array C

Array A is the old Windows installation, all the others are partitioned.

This is what I get after just setting language and keymap in the installer;

```
[0,416...] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[3,66...] sd 0:0:0:0: [sda] Assuming drive cache: write through
[3,66...] sd 0:0:0:0: [sda] Assuming drive cache: write through
[3,66...] sd 0:0:1:0: [sdb] Assuming drive cache: write through
[3,66...] sd 0:0:1:0: [sdb] Assuming drive cache: write through
[3,66...] sd 0:0:2:0: [sdc] Assuming drive cache: write through
[3,66...] sd 0:0:2:0: [sdc] Assuming drive cache: write through
[3,66...] sd 0:0:3:0: [sdd] Assuming drive cache: write through
[3,66...] sd 0:0:3:0: [sdd] Assuming drive cache: write through
```

The time tags at the beginning of the lines aren't that true, I just copied them roughly as I didn't think they were very important, if they are I can get a more accurate reading.

The server uses the IBM ServeRAID controller, and these disks are all mounted in hot-swappable slots in the front.

Hope we can get this sorted, this is going to be a big repository server for our Ubuntu desktop computers... :D I'm planning on mirroring the whole official repository on the C Array... :D

---

### Post by Stuggi on 2009-04-24
Okay, now I'm really pulling my hair here; I've reset all the controller's configurations, and the CMOS settings. I've also tried swapping out which controller I use for the discs vs. the tape drive, but nothing helps. I get the same error in Ubuntu no matter what controller I use. If I use the Adaptec controller instead of the IBM serveraid one I get a lot more output from the debian installer, but it still fails at the same time, it just takes more time. It does however detect the discs before failing, no idea if that's any use though...

---

### Post by m.ardito on 2009-09-25
Hi Stuggi

we are running a 9.04 on exactly the same machine, 
 type 8668 model 13G
with no problems.
Installed from desktop cd in livecd mode.
we installed from desktop and then stripped many desktop bells & whistles and ha from the start a gui, which we need as newbies :))

if you still need askme what you need to know.
just keep in mind i'm not an ubuntu expert

M

---

### Post by Stuggi on 2009-09-26
Okay, I just tried the server distro, I'll have to try the gui version next. :)

---


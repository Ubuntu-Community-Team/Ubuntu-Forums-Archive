---
title: "EXT3 SATA drivers for Windows API?"
date: 2006-12-26
forum: The Cafe
---

### Post by marco999 on 2006-12-26
Anyone know if there is any talk of making these? I know they are out for IDE devices but not for SATA.

marco999

---

### Post by .t. on 2006-12-26
The driver available is a filesystem driver. It doesn't care if it's IDE or SATA surely?

---

### Post by marco999 on 2006-12-26
Actually it does cause poor quality with SATA drives :( . I sent the guy an email and I hope he will fix it. The problem is simply that the drives will only be in PIO mode for SATA and that means that they are very limited to what tasks u can perform with them. For example a video file that is say 700 MB will not play smoothly off the drive. It will however save to the drive. Also if you copy say 33 GB to the drive or anything in the size of GB it will lag the computer.

Anyway thats what it does with SATA.

marco999

---

### Post by msdobrescu on 2009-02-28
May I ask where could I find the drivers? Oh which ext3 Windows drivers are you talking particularly?

---

### Post by gletob on 2009-02-28
Yeah could y'all explain what you're talking about it sounds like it might be interesting.

---

### Post by doorknob60 on 2009-02-28
OLD THREAD!!!! Anyways, see this: [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Polygon on 2009-02-28
that is a ext2 driver which causes problems for me with ext3 filesystems, god forbid what will happen with ext4 filesystems.

---

### Post by Cashel on 2009-03-23
They are talking about the explore2fs and Ext2 IFS projects probably.

Neither will currently read my ext3 since moving it to sata, sda2 is the partition but I only see hda5 (hda1 and 2 are my cdroms??) in explore2fs, and ext2 ifs asks me if I want to format it (it's always had ext3 bugs tho)..

So yea sata support would be nice :)

---

### Post by Skripka on 2009-03-23
> **Polygon said:**
> that is a ext2 driver which causes problems for me with ext3 filesystems, god forbid what will happen with ext4 filesystems.

Since we're digging up this 3 week old thread anyway....

The posted driver here for Windows for Ext2/3 does not work at all with Ext4, on my box.

---

### Post by smartboyathome on 2009-03-23
> **Skripka said:**
> Since we're digging up this 3 week old thread anyway....

The posted driver here for Windows for Ext2/3 does not work at all with Ext4, on my box.

That is because Ext4 cannot be mounted as EXT3 after a certain feature is enabled (which it is by default, and I can't remember which feature). So you are out of luck with EXT4 for now. :(

---

### Post by FuturePilot on 2009-03-23
> **smartboyathome said:**
> That is because Ext4 cannot be mounted as EXT3 after a certain feature is enabled (which it is by default, and I can't remember which feature). So you are out of luck with EXT4 for now. :(
[URL="http://en.wikipedia.org/wiki/Ext4#Extents"]
Extents[/URL]

---


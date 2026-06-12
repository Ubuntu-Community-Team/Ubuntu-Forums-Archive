---
title: "wipe data with /dev/random bash script"
date: 2015-01-12
forum: Security
---

### Post by jimmyh1972 on 2015-01-12
Hi, Iwrote this script:

#!/bin/bash
lsblk -d
A=$(`zenity --entry --text="enter your USB name"`)
sudo dd if=/dev/random of=/dev/"${A}" 

but after writing the name of /dev/sdX there is an stdo "dd: failed to open ‘/dev/’: Is a directory"
can anyone tell me what is the implementation problem?

thank's ahead - Jimmi

---

### Post by Lars Noodén on 2015-01-12
$A is an environment variable and root, via sudo, has a different environment from the common user launching sudo.  However, the script looks really, really unsafe in that entering the wrong device name will destroy either the system and or its data.  What kind of safeguards are you going to add to ensure that only external devices are targeted and that the main system, and possible data drives, are not targeted?

---

### Post by sudodus on 2015-01-12
If it is a hard disk drive, I suggest that you use [hdparm]("http://ubuntuforums.org/showthread.php?t=2124829") or ***DBAN***.

If it is a USB pendrive, I suggest that you use [mkusb to wipe the whole device]("https://help.ubuntu.com/community/mkusb#Wipe_the_whole_device").

---

### Post by HermanAB on 2015-01-13
A few notes:
1. Every hard disk has a secure erase utility in the drive controller that can erase the whole disk, including the space between tracks.  You can  exercise this utility with hdparm.
2. Solid state disks only need a simple format and erase using "mkfs.vfat /dev/sdxy", since they are not magnetic.
3. If you insist on trying to overwrite a file using a random number generator, then I suggest using /dev/urandom, since it is much faster, for the same bad results as using /dev/random.  The problem is that this will not overwrite the journal, bad blocks, or the space between tracks.

---


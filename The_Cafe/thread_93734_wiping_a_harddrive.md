---
title: "wiping a harddrive"
date: 2005-11-22
forum: The Cafe
---

### Post by dosed150 on 2005-11-22
how would i completly wipe all data on a hard drive   i need more hard drive space so im canibalising my old pc

---

### Post by Nu-Buntu on 2005-11-22
If you are adding it as a second drive to a current Ubuntu installation, just use gparted or qtparted. In Windows or DOS, try fdisk.

---

### Post by gord on 2005-11-22
you'll be looking for a command called 'format'.

---

### Post by dosed150 on 2005-11-22
yeh ill be adding it to this ubuntu pc from my old windows me pc

---

### Post by jdong on 2005-11-22
Put it in, then go to System->Administration->Disks... Select the new disk drive, and partition it accordingly.

Note that to extend onto this new disk, you have to use LVM. Other, you'll need to mount it to a new folder, and start putting stuff in there.

---

### Post by Dragineez on 2005-11-22
OOO! OOO! Call on me! I know the answer! Three weeks into converting to Linux and someone finally asked a question I know the answer to! Actually, I've gained an uncomfortable level experience with this, having done numerous install, nuke, reinstall cycles (just for fun you know, not to correct my FUs). If you **REALLY** want to totally nuke the disc, try shred.

---

### Post by professor_chaos on 2005-11-22
Or a big magnet.... :) :) :) :) ;)

---

### Post by narcolept on 2005-11-23
```
sudo fdisk /dev/drivelabel(just hda,hdb,etc)
```

Then follow the directions. erase all partitions, create a new partition(s). Write to disk, then make a filesystem

```
sudo mkfs -t ext3 /dev/hdwhatever
```

---

### Post by blastus on 2005-11-23
[DBAN](http://dban.sourceforge.net/). It's the best open source program out there.

---

### Post by migo on 2005-11-23
To wipe *all* data, you'll need to do a low level format, that's only an issue if you don't want it to be recoverable by any means.

---

### Post by narcolept on 2005-11-23
It sounds like the OP was just looking to clear out his disk in order to use it as a linux partition.

---

### Post by dosed150 on 2005-11-23
yeh thats what i want to have it as a second harddrive on this ubuntu system

thanx everyone

---


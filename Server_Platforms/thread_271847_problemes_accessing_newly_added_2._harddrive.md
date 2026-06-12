---
title: "problemes accessing newly added 2. harddrive"
date: 2006-10-05
forum: Server Platforms
---

### Post by water on 2006-10-05
I've just installed Ubuntu server to replace ClarkConnect 2.2 on my Slimserver box.

The new installation is up and running and I've added the my second harddrive (that hold all my music) and added this line

> /dev/hdb1 /storage ext3 auto 1 2to /etc/fstab which is the same line I had in /etc/fstab on my old ClarkConnect installation, this however does not work as I expected.

running : > sudo fdisk /dev/hdb1 -ugives this result : > 
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel. Changes will remain in memory only,
until you decide to write them. After that, of course, the previous
content won't be recoverable.


The number of cylinders for this disk is set to 24320.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
(e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)


I'm reluctant to use the w(rite) commando as I'm not sure what it will actually do and I really don't want to wipe my harddrive...

I've also considered reinstalling Ubuntu server with the disk installed in the box, but I'm afraid it might be wiped if something goes wrong during the intall

Can anybody point me in the right direction or give any recommendations?

:water

---

### Post by sonic2000gr on 2006-10-05
Could you please do a

```
sudo fdisk -l 
```

and paste the results here? (this is a small letter L not 1...)

---

### Post by water on 2006-10-05
> sudo fdisk -lgives :

> Disk /dev/hda: 10.2 GB, 10245537792 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1190     9558643+  83  Linux
/dev/hda2            1191        1245      441787+   5  Extended
/dev/hda5            1191        1245      441756   82  Linux swap / Solaris

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       24321   195358401   83  Linux



hdb is the un-accessable disc.

:water

---

### Post by sonic2000gr on 2006-10-05
Try something like the following:

```
sudo mount -t ext3 /dev/hdb1 /mnt
```

and paste any message it produces.

---

### Post by water on 2006-10-06
that did it - Thanks!

(kind of embaresed now that I didn't think of that, for some reason I was sure the disk would auto-mount...)


:water

---

### Post by sonic2000gr on 2006-10-06
You should be able to mount it from fstab as you originally planned:

-Make sure the mount point exists or create it first (i.e. sudo mkdir /storage )

-Add the following line to fstab:

```
 /dev/hdb1   /storage    ext3   defaults   0  0 
```

Execute the following command:

```
 sudo mount -a 
```

See if it works!

---


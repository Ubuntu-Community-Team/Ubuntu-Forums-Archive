---
title: "45Gb of disk space lost!"
date: 2010-12-12
forum: Server Platforms
---

### Post by PryGuy on 2010-12-12
Good day everyone!
I've got a terrabyte HDD on my server used as a data storage formatted as ext3. There's no space left on the device Samba said. Indeed, df shows that all the 100% were used:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             917G  872G     0 100% /media/sdb1
```
But where's the 45 (fourty five!) gigabytes? fsck says file system is clean.

Thanks in advance!

---

### Post by JustinR on 2010-12-12
It's in use by the filesystem itself for file purposes.

You can disable it though to free up some, but not all of the space with the program 'tune2fs'.

---

### Post by PryGuy on 2010-12-12
> **JustinR said:**
> It's in use by the filesystem itself for file purposes.
1. Well, I knew that, but are you sure all the 45 gigabytes were used for the purposes? That appears to be too much.
2. Are you sure df shows all the size including the non usable amount and not the space I can use?

Yet, how come I still could copy over 10GB on this device using mc? (just did it) and it was shown in the console that:
```
  => /media/sdb1 is using 95.0% of 916.89GB
```when I logged in.

---

### Post by JustinR on 2010-12-12
> **PryGuy said:**
> 1. Well, I knew that, but are you sure all the 45 gigabytes were used for the purposes? That appears to be too much.
2. Are you sure df shows all the size including the non useable amount and not the space I can use?

Yes, on an EXT4 filesystem is could take up over 100GBs.

---

### Post by HermanAB on 2010-12-12
Howdy,

Ext3/4 can use up to 15% of the disk for the journal.  JFS and XFS are more efficient.

---

### Post by dtfinch on 2010-12-12
"sudo tune2fs -m0 /dev/sdb1" would change the reserved amount from 5% to 0%.

edit/add: The journal is a fixed size, and much smaller. On mine it's 128mb, which seems to be the maximum size it'll create by default. The 5% reservation was supposedly to give the admin/root some breathing room if something unexpectedly filled up the drive. Reserving 5% made more sense when most hard drives were 1-10gb, but not so much nowadays. I usually leave it at 1% (tune2fs -m1 ...).

---

### Post by Spice Weasel on 2010-12-12
There's a number of reasons for this - 

Drive manufacturers give you the unformatted drive size (so it wasn't 1TB in the first place)

The ext file system uses space for the journal.

---

### Post by PryGuy on 2010-12-12
Thanks people, especially dtfinch, your answer was very helpful! ;)

---

### Post by Vegan on 2010-12-12
All journalling file systems have overhead for the journal. The reason is its a backup of what was done, so a repair tool only needs to read the journal back to fix files.

NTFS uses a lot of space too, about the same as EXT4 on my web server.

No problem, when in doubt, buy another disk or 3

---


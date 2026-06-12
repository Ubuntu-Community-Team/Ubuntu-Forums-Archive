---
title: "commands for checking bad sectors and formatting with cli, plz help"
date: 2008-05-29
forum: Server Platforms
---

### Post by garethsimpsonuk on 2008-05-29
can someone plz tell me how to format, check for bad sectors, and create partitions with the cli.
I cant do anything till i get this sorted all i wanna do is format my sdb as 1 big partition and fix any errors in the drive.

any ideas guys?

thanx

---

### Post by bluefrog on 2008-05-29
use parted

sudo parted /dev/sdb

---

### Post by garethsimpsonuk on 2008-05-29
ok cool thanx,

i get about a page of errors for this disk ( which end in this )

status:   drdy err
error:   icrc abrt 

does anyone know what these mean? are they bad sectors on the disk? if so can they be repaired? is it a bad idea using this for storage? it lets me install an os straght on to it but when i boot that os i get this:

29.843937 ldm_validate_partition_table(): disk read failed 
( similar errors to boot up ones ) 

what tools can i use to try and repair this guys? thanx for your help

---

### Post by garethsimpsonuk on 2008-05-29
i read the man 

i ran fsck -a /dev/sdb

fsck.ext2: bad magic number in super-block while trying to open /dev/sdb
/dev/sdb:
the superblock could not be read or does not describe a correct ext2 filesystem. if the device is valid and it really contains an ext2 filesystem ( it's ext3 ), then the superblock is corrupt, and you might try running e2fsck with an alternative superblock

so...

sudo e2fsck -b 8193 /dev/sdb

device or resource busy while trying to open /dev/sdb
Filesystem mounted or opened exclusively by another program?

What do I do here? it's not mountes as far as i'm aware..

plz help oh wonderful ubuntu gods

---

### Post by garethsimpsonuk on 2008-05-29
cmon guys I know you lot can fix it for me!

---

### Post by MJN on 2008-05-29
> **garethsimpsonuk said:**
> i read the man 

i ran fsck -a /dev/sdb

fsck.ext2: bad magic number in super-block while trying to open /dev/sdb
/dev/sdb:
the superblock could not be read or does not describe a correct ext2 filesystem. if the device is valid and it really contains an ext2 filesystem ( it's ext3 ), then the superblock is corrupt, and you might try running e2fsck with an alternative superblock
fsck is for checking file systems, and they reside only in partitions hence you need to specify the partition and not just the drive.

To list the partitions on the drive, run **sudo fdisk -l /dev/sdb** then check each partition with **sudo fsck -a /dev/sdb1** (for example, but see below for fs-specific tools).

You might want to read up on the fsck specific to your filesystem (e.g. e2fsck for ext2/3, giving you features such as block checking/marking with -c) and this will include options specific to the format (fsck just calls the necessary checker, and passes the arguments to it).

Mathew

---

### Post by gtdaqua on 2008-05-30
gareth, post your output of 

```

sudo fdisk -l

```

If you want to straight format the new drive (/dev/sdb), first unmount using "umount" command (if you have it mounted, of course). Then type:

```

sudo fdisk /dev/sdb

```

Can you take it from there or need a walkthorugh?

---

### Post by garethsimpsonuk on 2008-06-02
Thanks for the reply mate, soz I've been away from Ubuntu for a few days as I gave up on the drives. Some of them are from 2002 do you think they've been working long enough? Anyway I've decided they must be dying so I've forked out for 200GB, 500GB SATA drives from ebay and I will install them instead and then try and see which of the 6 IDE drives piled up on my desk actually still work. If I have 2 SATA drives & 4 IDE drives am I pushing an old athlon xp 2000 too much do you think? would I need a new power suypply? I'm just looking now on ebay for a pci SATA controller that will work with Ubuntu, I'm worried the VIA VT6421A may have problems,  I'm still researching. If anyone has any experience with this chipset plz let me know.
Thanks,

By the way I've been working on setting up XBMC on old xboxes while I'm ubuntuless and it's great. When I have evrything set up on my home network it's gonna be amazing.

---

### Post by MJN on 2008-06-02
After six years they certainly don't owe you anything, and indeed you are arguably living on borrowed time. I think you've made the right decision in replacing them, and you'll benefit from the performance/capacity benefits too.
 
I'm afraid I cannot help on the power front, although it is a consideration you need to bear in mind. It does of course depend on the capacity of the existing supply and the intended usage patterns of the drives (although you don't want to be relying on the latter if you're pushing the limit of the supply).
 
Mathew

---

### Post by garethsimpsonuk on 2008-06-02
yea you're right. at least they went now instead of further down the line when they would've been the whole storage for the whole family. I was stupid to even think on relying on them drives.
I'm still stuck on a SATA controller (PCI) though. I posted in the server boards to and no replies. 
I only want a cheap card and all the lower priced ones on ebay seem to have the VIA VT6421A chipset which according to launchpad and a few forum users, worked in 7.04 and stopped working in 7.10. I'm running hardy and don't wanna get this chipset if it don't work. Unfortunately tghe posters didn't put a final courtesy post on the outcome for any future reference. I can look for more expensive ones if I need to but I need some advice or at least a pointer on where to get advice.
Any1 got any ideas? Surely SATA controllers are a priority for the devs and most should be fine? Are there some budget chipsets that are linux friendly?

Cheers

---


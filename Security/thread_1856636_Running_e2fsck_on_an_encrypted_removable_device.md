---
title: "Running e2fsck on an encrypted removable device"
date: 2011-10-08
forum: Security
---

### Post by /dev/n on 2011-10-08
Not sure if I'm posting this in the right section, but here it goes.

I have an encrypted flash drive (ecryptfs) and it's begun to complain in dmesg

```

EXT4-fs (dm-1): warning: maximal mount count reached, running e2fsck is recommended

```

but I'm at a loss how to do it. Manpage with its options is typical gibberish to this blockhead. Still, I'd definitely like to run that check to make sure the encrypted partition won't be damaged at some point and none of the important data get lost in the process. When mounted, the drive will show up as either /dev/sdb or /dev/sdc, but if it's unmounted/still encrypted and I try for example
```

e2fsck -n /dev/sdb1

```
it just blurts out
```

e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

and I'm none the wiser. Is there any way to do it correctly, or do I have to always reformat/repartition that drive, encrypt the partition and copy the data back onto it, until the maximum mount count warning reappears, and do it all over again?

---

### Post by OpSecShellshock on 2011-10-08
I threw the error into Google, which is what I'd recommend since the results are plentiful (and largely redundant, it seems). The message doesn't really appear to be an error, actually, more of a suggestion, but I'm not absolutely certain. It appears that certain types of file systems have a setting which will cause this message to come up every 30 times they are mounted. Something similar actually happens when I boot up my system every so often, in that it runs a file system check during startup, but it happens on its own. I suppose it's possible with removable storage that it needs to be done manually. Over time, corruption happens and it's best to check for it, is the sense I'm getting from what I've read in the last couple minutes.

EDIT: Oh, and I think you're getting the message from e2fsck because it's expecting an ext2 file system but the format of your drive is ext4.

---

### Post by FuturePilot on 2011-10-08
> **/dev/n said:**
> Not sure if I'm posting this in the right section, but here it goes.

I have an encrypted flash drive (ecryptfs) and it's begun to complain in dmesg

```

EXT4-fs (dm-1): warning: maximal mount count reached, running e2fsck is recommended

```

but I'm at a loss how to do it. Manpage with its options is typical gibberish to this blockhead. Still, I'd definitely like to run that check to make sure the encrypted partition won't be damaged at some point and none of the important data get lost in the process. When mounted, the drive will show up as either /dev/sdb or /dev/sdc, but if it's unmounted/still encrypted and I try for example
```

e2fsck -n /dev/sdb1

```
it just blurts out
```

e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

and I'm none the wiser. Is there any way to do it correctly, or do I have to always reformat/repartition that drive, encrypt the partition and copy the data back onto it, until the maximum mount count warning reappears, and do it all over again?

Are you sure this drive is encrypted with ecryptfs? Or is it LUKS?

---

### Post by /dev/n on 2011-10-09
> **OpSecShellshock said:**
> The message doesn't really appear to be an error, actually, more of a suggestion, but I'm not absolutely certain. It appears that certain types of file systems have a setting which will cause this message to come up every 30 times they are mounted. Something similar actually happens when I boot up my system every so often, in that it runs a file system check during startup, but it happens on its own. I suppose it's possible with removable storage that it needs to be done manually. Over time, corruption happens and it's best to check for it, is the sense I'm getting from what I've read in the last couple minutes. 

I know it's **only** a suggestion at this point, and I'd like to be able to check the partition before any actual errors come up that threaten the data stored on the partition. Sure I know about and have witnessed the file system check at startup numerous times, but for an encrypted removable device, it doesn't run automatically like that (or I don't know how to set it up, hence my call for help). 

> 
EDIT: Oh, and I think you're getting the message from e2fsck because it's expecting an ext2 file system but the format of your drive is ext4.

e2fsprogs should handle not only ext2 but ext3 and ext4 as well (at least according to its description in Synaptic). After all, isn't it the same program that checks the hard drive partitions?

@ FuturePilot:

I may have been a bit confused. I used the gnome-disk-utility (palimpsest) to originally format the flash drive and create the encrypted partition. It's just that ecryptfs was required for it to work.

---

### Post by FuturePilot on 2011-10-09
> **/dev/n said:**
> 

@ FuturePilot:

I may have been a bit confused. I used the gnome-disk-utility (palimpsest) to originally format the flash drive and create the encrypted partition. It's just that ecryptfs was required for it to work.

That's definitely encrypted with LUKS. I'm not sure how it would be tied to ecryptfs though. (maybe installing ecryptfs pulled in cryptsetup?) Anyway, you need to unlock it before you can fsck it.

```
sudo cryptsetup luksOpen /dev/sdb1 foo
```
You can use whatever name you want for foo. It should ask you then for the password. Then you can run
```
sudo fsck /dev/mapper/foo
```
Though, if you're using Gnome there may be a possibility that it's already unlocked if you have allowed gnome-keyring to save the password. In that case you just have to find it in /dev/mapper. It's probably the one that begins with udisks-luks-uuid. Just make sure it's unmounted first.
```
sudo umount /dev/mapper/udisks-luks-uuid-blahblahblah
```

> **OpSecShellshock said:**
> 

EDIT: Oh, and I think you're getting the message from e2fsck because it's expecting an ext2 file system but the format of your drive is ext4.
e2fsck is part of e2fsprogs. I'm not sure why they kept the e2 name but it works with all Ext file systems.

---

### Post by /dev/n on 2011-10-09
Okay, so when I ran

```

sudo cryptsetup luksOpen /dev/sdb1 foo

```
it responded
```

device-mapper: remove ioctl failed: Device or resource busy
Key slot 0 unlocked.

```
mounted the partition (should it have?) and opened it, so I manually unmounted it and then tried
```

sudo fsck /dev/mapper/szs

```
with the following output:

```

e2fsck 1.41.11 (14-Mar-2010)
/dev/mapper/szs has been mounted 29 times without being checked, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/mapper/szs: 2031/62720 files (0.1% non-contiguous), 53513/250878 blocks

```

It was done really quickly, in a few seconds, so I wonder if it actually checked everything. Apparently, no errors were found.

---

### Post by OpSecShellshock on 2011-10-09
> **FuturePilot said:**
> 
e2fsck is part of e2fsprogs. I'm not sure why they kept the e2 name but it works with all Ext file systems.

I gotcha. I figured that it was either the format or the encryption, and it seems to have been the encryption, which makes sense.

---

### Post by FuturePilot on 2011-10-09
> **/dev/n said:**
> Okay, so when I ran

```

sudo cryptsetup luksOpen /dev/sdb1 foo

```
it responded
```

device-mapper: remove ioctl failed: Device or resource busy
Key slot 0 unlocked.

```
mounted the partition (should it have?) and opened it, so I manually unmounted it and then tried
```

sudo fsck /dev/mapper/szs

```
with the following output:

```

e2fsck 1.41.11 (14-Mar-2010)
/dev/mapper/szs has been mounted 29 times without being checked, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/mapper/szs: 2031/62720 files (0.1% non-contiguous), 53513/250878 blocks

```

It was done really quickly, in a few seconds, so I wonder if it actually checked everything. Apparently, no errors were found.

No it definitely checked everything. Running fsck on Ext4 is extremely fast because it doesn't have to check unused space.

---

### Post by /dev/n on 2011-10-10
> **FuturePilot said:**
> No it definitely checked everything. Running fsck on Ext4 is extremely fast because it doesn't have to check unused space.

All right then. Thanks a lot for your help. Now when I mounted the encrypted partition again, dmesg no longer complained about maximal mount count, so it worked. Have a safe flight.

---


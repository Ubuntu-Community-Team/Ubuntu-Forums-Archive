---
title: "How to mount a dm-crypt/luks drive"
date: 2011-04-04
forum: Security
---

### Post by fireflytech on 2011-04-04
Hi

I have a perfectly OK 2.5 inch disk drive from a dead laptop (graphics card failed).

The hard drive is fine. I know the passphrase.

I had installed Ubuntu 10.04 with full fisk encryption using dm-crypt/luks using the alternate install cd.

I'm not exactly sure of the configuration I selected. Just that its full disk encryption with a pre-boot passphrase prompt.

Now my issue is, I have put the drive into a usb drive docking station, and I simply want to mount the partition on my new laptop, so I can copy the files over.

I've tried googling for various things like "mount dm-crypt drive linux" and "how to mount a luks encrypted partition linux", but I get no results.

Any help would be appreciated, including suggestions as to what I need to be searching for. I have no idea.

---

### Post by FuturePilot on 2011-04-04
If you have it in a USB converter it should just recognise and ask you for the passphrase.

---

### Post by fireflytech on 2011-04-04
Ok I have more info now.

I've got ubuntu 10.10 livecd running on my macbook (which is the working laptop)

When I plug the drive in, I get various partitions trying to mount. There are at least two main partitions on the drive. An unencrypted Windows partition of 105GB that mounts OK and immediately.

Then the 215GB dm-crypt/luks encrypted partition.

```

root@ubuntu:/home/ubuntu# fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00002f68

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60802   488386583+  ee  GPT

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003cd60

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       12749   102400000    7  HPFS/NTFS
/dev/sdc2           12749       12780      248832   83  Linux
/dev/sdc3           12780       38914   209920001    5  Extended
/dev/sdc5           12780       38914   209920000   83  Linux


```



```

root@ubuntu:/home/ubuntu# lvmdiskscan 
  /dev/dm-0: read failed after 0 of 4096 at 214956900352: Input/output error
  /dev/dm-0: read failed after 0 of 4096 at 214957019136: Input/output error
  /dev/dm-0: read failed after 0 of 4096 at 0: Input/output error
  /dev/dm-0: read failed after 0 of 4096 at 4096: Input/output error
  /dev/dm-1: read failed after 0 of 4096 at 7998472192: Input/output error
  /dev/dm-1: read failed after 0 of 4096 at 7998529536: Input/output error
  /dev/dm-1: read failed after 0 of 4096 at 0: Input/output error
  /dev/dm-1: read failed after 0 of 4096 at 4096: Input/output error
  /dev/dm-2: read failed after 0 of 4096 at 206955282432: Input/output error
  /dev/dm-2: read failed after 0 of 4096 at 206955339776: Input/output error
  /dev/dm-2: read failed after 0 of 4096 at 0: Input/output error
  /dev/dm-2: read failed after 0 of 4096 at 4096: Input/output error
  /dev/sdc1: read failed after 0 of 4096 at 0: Input/output error
  /dev/sdc5: read failed after 0 of 4096 at 4096: Input/output error
  /dev/ram0  [      64.00 MiB] 
  /dev/loop0 [     660.59 MiB] 
  /dev/dm-0: read failed after 0 of 4096 at 0: Input/output error
  /dev/dm-0: read failed after 0 of 4096 at 0: Input/output error
  /dev/ram1  [      64.00 MiB] 
  /dev/sda1  [     200.00 MiB] 
  /dev/dm-1: read failed after 0 of 4096 at 0: Input/output error
  /dev/dm-1: read failed after 0 of 4096 at 0: Input/output error
  /dev/ram2  [      64.00 MiB] 
  /dev/sda2  [     464.96 GiB] 
  /dev/dm-2: read failed after 0 of 4096 at 0: Input/output error
  /dev/dm-2: read failed after 0 of 4096 at 0: Input/output error
  /dev/ram3  [      64.00 MiB] 
  /dev/sda3  [     624.23 MiB] 
  /dev/ram4  [      64.00 MiB] 
  /dev/ram5  [      64.00 MiB] 
  /dev/ram6  [      64.00 MiB] 
  /dev/ram7  [      64.00 MiB] 
  /dev/ram8  [      64.00 MiB] 
  /dev/ram9  [      64.00 MiB] 
  /dev/ram10 [      64.00 MiB] 
  /dev/ram11 [      64.00 MiB] 
  /dev/ram12 [      64.00 MiB] 
  /dev/ram13 [      64.00 MiB] 
  /dev/ram14 [      64.00 MiB] 
  /dev/ram15 [      64.00 MiB] 
  /dev/sdc1  [      97.66 GiB] 
  /dev/sdc2  [     243.00 MiB] 
  /dev/sdc5  [     200.20 GiB] 
  0 disks
  23 partitions
  0 LVM physical volume whole disks
  0 LVM physical volumes
root@ubuntu:/home/ubuntu# 

```

```

root@ubuntu:/home/ubuntu# ls -la /dev/mapper/
total 0
drwxr-xr-x  2 root root    120 2011-04-05 02:56 .
drwxr-xr-x 20 root root   3960 2011-04-05 02:57 ..
crw-------  1 root root 10, 59 2011-04-05 02:41 control
lrwxrwxrwx  1 root root      7 2011-04-05 02:47 udisks-luks-uuid-00bf5c8d-2e27-4751-990a-d84c5658dd2e-uid999 -> ../dm-0
lrwxrwxrwx  1 root root      7 2011-04-05 02:56 volgroup-root -> ../dm-2
lrwxrwxrwx  1 root root      7 2011-04-05 02:56 volgroup-swap -> ../dm-1
root@ubuntu:/home/ubuntu# 

```


I've apt get installed lvm2 as I now understand this has something to do with unencrypting the partion, and then mounting the lvm partitions after that.

I think.

---

### Post by srs5694 on 2011-04-05
The "input/output error" messages indicate that either the disk is *not* "perfectly OK," as you stated in your original post, or that you've got a problem with your USB adapter. I recommend you try it on another computer, with a different USB adapter, or plugged directly into a computer (without the adapter).

---

### Post by MountainX on 2011-04-11
> **srs5694 said:**
> The "input/output error" messages indicate that either the disk is *not* "perfectly OK," as you stated in your original post, or that you've got a problem with your USB adapter. .

Or it could also indicate that the disk has not been decrypted and/or the logical volumes have not been activated.

I'm guessing that you have encrypted volumes inside your logical volume

Get a picture of your volume with these commands:
$ sudo pvscan
$ sudo pvs
$ sudo vgscan
$ sudo vgs
$ sudo cat /etc/crypttab

reviewing the above info will help you figure out what's on your disk.

To make all volume groups active, run this command:
$sudo vgchange -a y

to decrypt your encrypted volumes, you'll probably need something like this:
$ sudo cryptsetup luksOpen /path/to/volume mappingName

pattern for above command: cryptsetup luksOpen /dev/vg/lv mappingName

In summary, the errors do not necessarily indicate a hardware or drive problem. You need to mount encrypted LVM volumes in two steps:
1. activate the volume group and mount the logical volume(s)
2. decrypt

---


---
title: "Problems with cryptsetup after installing Jaunty: Can not access device"
date: 2009-05-21
forum: Security
---

### Post by helgar on 2009-05-21
Hello!

after updating to Jaunty, I have problems with cryptsetup and like to ask for your help.

I have three internal hard disks. My system is installed on sdc. The disks sda and sdb do have one partition each which is encrypted using cryptsetup. After installing Jaunty, I cannot access sda1 and sdb1 anymore. 

When I do: 
[INDENT]cryptsetup luksOpen /dev/sda1 cryptsda1
Command failed: Can not access device
[/INDENT]fdisk says about sda:

[INDENT]Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       36481   293033601   83  Linux


[/INDENT]but in /proc/partitions, sda1 and sdb1 do not apprear:

[INDENT]cat /proc/partitions 
major minor  #blocks  name

   8        0  293036184 sda
   8       16  293036184 sdb
[/INDENT]
so, somehow the kernel does not know about the partition. So I did:

[INDENT]hdparm -z /dev/sda

/dev/sda:
 re-reading partition table
[/INDENT]
for both, sda and sdb.

After that, they appear in /proc/partitions:

[INDENT]cat /proc/partitions 
major minor  #blocks  name

   8        0  293036184 sda
   8        1  293033601 sda1
   8       16  293036184 sdb
   8       17  293033601 sdb1
[/INDENT]
And when I have a look at luksDump:

[INDENT]cryptsetup luksDump /dev/sda1
[/INDENT]
[INDENT]LUKS header information for /dev/sda1

Version:           1
Cipher name:       aes
Cipher mode:       cbc-essiv:sha256
[...]
[/INDENT]
so, cryptsetup knows now that sda1 is an encryptet partition. But when I try to open it, I still get:

[INDENT]cryptsetup luksOpen /dev/sda1 cryptsda1
Command failed: Can not access device
[/INDENT]
I don't know what else to do - any ideas?

I can open other partitions, for example on sdc or on external usb-disks, just not these two. 

Thanks for any advice!

helgar

---

### Post by ztripez on 2009-06-01
I got the same issue. Upgraded to Jaunty and now my luks cryptet partitions doesn't work. 
LOTS of importnant data that i just have to get back..

---

### Post by unutbu on 2009-06-01
ztripez, what is the output of 
```

lsmod | grep dm-crypt
```

---

### Post by nunki on 2009-06-01
By chance does your /etc/crypttab have incorrect entries in it? Perhaps it refers to the disks UID as opposed to its name?

---

### Post by helgar on 2009-06-07
Hi!

I still got the problem, I got a little further, but no solution yet. 

I tried to run cryptsetup with strace and the first time I get the output:

[...] ioctl(3, DM_TABLE_STATUS, 0×9353a00)    = -1 ENXIO (No such device or address)
open(”/dev/sda1&#8243;, O_RDONLY|O_EXCL|O_SYNC|O_DIRECT|O_LARGEFILE) = -1 ENOENT (No such file or directory) [...]

After re-reading the partition table it gets:

[...] ioctl(3, DM_TABLE_STATUS, 0×9191a00)    = -1 ENXIO (No such device or address)
open(”/dev/sda1&#8243;, O_RDONLY|O_EXCL|O_SYNC|O_DIRECT|O_LARGEFILE) = -1 EBUSY (Device or resource busy) [...]

I tried to find out, what captures the device. dmesg did not say anything about it, so I ran[INDENT]lsof | grep sda
[/INDENT]and got the output:[INDENT]lsof: WARNING: can’t stat() fuse.gvfs-fuse-daemon file system /home/helgar/.gvfs
Output information may be incomplete.
[/INDENT]I do not really know what that means, but I killed the fuse-daemon to see what happens, but nothing changes.

Unutbu, I tried[FONT=monospace]
lsmod | grep dm-crypt 
but received no output. 

In my crypttab, there is no entry regarding sda at all. 

Any clues?
[/FONT]

---

### Post by unutbu on 2009-06-07
helgar, the dm-crypt module must be loaded into the kernel for you to be able to read LUKS-encrypted partitions.

If 
```

lsmod | grep dm-crypt
```

returns nothing, then that means dm-crypt is not loaded into the kernel.

To load the dm-crypt module run this:
```

sudo modprobe dm-crypt
```

Then try 
```

cryptsetup luksOpen /dev/sda1 cryptsda1
```

again. If that succeeds, look for /dev/mapper/cryptsda1. And if that is there, then
try 
```

sudo mount /dev/mapper/cryptsda1 /mnt
```

If all that works then your sda1 filesystem should be mounted at /mnt.

To make dm-crypt load at boot time, edit /etc/modules and add

```
dm-crypt
```

on a line by itself at the end of the file.

See also [http://ubuntuforums.org/showthread.php?t=404346](http://ubuntuforums.org/showthread.php?t=404346)
[http://ubuntuforums.org/showpost.php?p=7399077&postcount=13](http://ubuntuforums.org/showpost.php?p=7399077&postcount=13)

---

### Post by tigrino on 2009-06-17
damn... don't you wish sometimes you could know the problems beforehand?

Ok, all of the above advice is of no use. After moving the USB disk from the machine 8.04 to machine 9.04 I cannot read the encrypted disk. Same message as the person above. Grrr... Is downgrading the only possible fix?

---

### Post by HDave on 2010-02-23
This problem just starting happening to me on 9.04 -- don't know if it was an upgrade, but I can't open my old luks partitions either.  Not good!

Did you ever get to the bottom of this?

---


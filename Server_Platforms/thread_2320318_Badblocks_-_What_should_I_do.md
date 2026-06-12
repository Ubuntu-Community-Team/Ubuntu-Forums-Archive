---
title: "Badblocks - What should I do?"
date: 2016-04-12
forum: Server Platforms
---

### Post by sed_faster on 2016-04-12
Hello everyone,

I think if this place correct to put my doubt. But please, if I am in wrong place please guided me, thanks!
Used the program badblocks for first time. I read the documentation in man badblocks and chose this set "sudo badblocks -o file.txt -svw /dev/sdX"

Two doubts:
1-That is supposedly will made any thing after the still over? (It is stilling run, go away almost two hours, the disk has 250GB);
2-The file "file.txt" was 1.7GB. How open this file, because of its size I can't open to analysing.

What you advice?

INFO: Ubuntu Server 14.04 LTS
Thanks
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
I am a enthusiastic to electronic, computers and programs. If you have  any idea or doubt about the algorithmic/programmer in shell script  please send email to edgaroliveira.devatgmaildotcom. I promise which I  try help you.
I am improve my English, if couldn't understand anything which I wrote  please give the opportunity to do better and talk with my through  comment. Anyway, please give me your rating, of course, if you want and  powers.

---

### Post by Graham_Willis on 2016-04-12
But what exactly is the problem with opening this file? I've just opened a file which is 8x as big as RAM in my computer with **less** command. If for some reason less solution doesn't work for you, consider using **split** in order to break this large file into pieces. Also, you can always use **head**/**tail**, it'll at least enable you to look at a part of this file.

---

### Post by SeijiSensei on 2016-04-13
Writing the list of bad blocks to a file as you did doesn't really accomplish anything.  If there really are bad blocks, you can reformat the drive to ignore them with the command
```
sudo mkfs -c -t ext4 /dev/sdb1
```
to format the first partition ("1") on the second hard drive ("b").

That will examine the drive for badblocks and mark any it finds as unwritable while formatting.  This process can take hours on any large device. And, of course, it will destroy all the data in the filesystem, so you would need to back it up first.

If the problematic area of the drive contains the operating system, you cannot run this command directly on the machine itself since you would be reformatting the operating system while it is in use.  Rather you will have to boot from a Ubuntu disk image using "Try Ubuntu" and run the command from there.

---

### Post by sed_faster on 2016-04-21
Thanks all help,

I used command "sudo mkfs -c -t ext4 /dev/sdd". I don't know how analyse the data provide the command badblocks.
 After the format device I used the fdisk /dev/sdd to create a partition. My fdisk is:

> Disk /dev/sdd: 500.1 GB, 500107862016 bytes
81 heads, 63 sectors/track, 191411 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x45810833

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048   976773167   488385560   83  Linux

But when I tried mount the partition I couldn't because "mount: you must specify the filesystem type". I tried "sudo mount /dev/sdd1 /media/5001 -t ext4" and received this message:

> mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I executed this command: "dmesg | tail -n 30" and can saw which I has problem with any partition, but why if occur? And how should I interpretation this?

> [ 1550.222353] EXT4-fs (sdd4): unable to read superblock
[ 1550.222562] EXT4-fs (sdd4): unable to read superblock
[ 1550.224736] FAT-fs (sdd4): invalid media value (0x00)
[ 1550.224811] FAT-fs (sdd4): Can't find a valid FAT filesystem
[ 1919.143997] usb 3-3: USB disconnect, device number 2
[ 1924.800130] usb 3-3: new low-speed USB device number 3 using ohci-pci
[ 1925.034179] usb 3-3: New USB device found, idVendor=04d9, idProduct=1702
[ 1925.034194] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1925.034198] usb 3-3: Product: USB Keyboard
[ 1925.034201] usb 3-3: Manufacturer:  
[ 1925.070228] input:   USB Keyboard as /devices/pci0000:00/0000:00:1c.1/usb3/3-3/3-3:1.0/0003:04D9:1702.0003/input/input7
[ 1925.126366] hid-generic 0003:04D9:1702.0003: input,hidraw0: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:1c.1-3/input0
[ 1925.179527] input:   USB Keyboard as /devices/pci0000:00/0000:00:1c.1/usb3/3-3/3-3:1.1/0003:04D9:1702.0004/input/input8
[ 1925.232830] hid-generic 0003:04D9:1702.0004: input,hidraw1: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:1c.1-3/input1
[ 2062.056976] perf interrupt took too long (5049 > 5000), lowering kernel.perf_event_max_sample_rate to 25000
[ 5216.052570] nfsd: last server has exited, flushing export cache
[ 6344.910023] usb 3-3: USB disconnect, device number 3
[33788.130211]  sdd: sdd1
[34034.207509] EXT4-fs (sdd1): VFS: Can't find ext4 filesystem
[34034.208402] EXT4-fs (sdd1): VFS: Can't find ext4 filesystem
[34034.209004] EXT4-fs (sdd1): VFS: Can't find ext4 filesystem
[34034.209664] FAT-fs (sdd1): bogus number of FAT structure
[34034.209717] FAT-fs (sdd1): Can't find a valid FAT filesystem
[34043.632001] EXT4-fs (sdd1): VFS: Can't find ext4 filesystem
[34086.761936] EXT4-fs (sdd1): VFS: Can't find ext4 filesystem
[34086.762497] EXT4-fs (sdd1): VFS: Can't find ext4 filesystem
[34086.762985] EXT4-fs (sdd1): VFS: Can't find ext4 filesystem
[34086.763604] FAT-fs (sdd1): bogus number of FAT structure
[34086.763657] FAT-fs (sdd1): Can't find a valid FAT filesystem
[34138.898316] EXT4-fs (sdd1): VFS: Can't find ext4 filesystem

Lastly, I tried mount the disk just like that: "sudo mount /dev/sdd /media/5001" And it's works! Why?
Thanks

---

### Post by SeijiSensei on 2016-04-21
/dev/sdd refers to the entire drive.  It cannot have a valid filesystem.  You need to format a partition like /dev/sdd1, the first partition on drive /dev/sdd.

Go back to fdisk, create a partition (with "n") and accept the defaults to make the partition span the entire drive.  Then run
```
sudo mkfs -c -t ext4 /dev/sdd1
```
and mount that instead.

---

### Post by sed_faster on 2016-04-25
hello,

I could resolve! When did "sudo fdisk /dev/sdd" and chosen the option n I shoulder choose option p0 to primary. But I chosen only p, and the system only allows format entire drive.

Just a matter, how should I search the uuid name? Should do "sudo blkid /dev/sdd" or "sudo blkid /dev/sdd1"

thanks

---

### Post by sed_faster on 2016-04-25
> **SeijiSensei said:**
> /dev/sdd refers to the entire drive.  It cannot have a valid filesystem.  You need to format a partition like /dev/sdd1, the first partition on drive /dev/sdd.

Go back to fdisk, create a partition (with "n") and accept the defaults to make the partition span the entire drive.  Then run
```
sudo mkfs -c -t ext4 /dev/sdd1
```
and mount that instead.

My fstab it is that:

```

UUID=e85771e4-fed0-422d-83dd-a857b6ac7ce8       /media/160      ext4    defaults        1       1
UUID=995dfb0e-119d-43db-96f5-7d2d8c854125       /media/5001     ext4    defaults      1       2
UUID=a1b72ed6-69e8-40c6-9531-9ee064bf855a       /media/5002     ext4    defaults      1       3

```

Which /media/160 I haven't problem, my client can write on this folder through nfs server. But on the 5001 and 5002 he didn't can write. So, I set the parameter uid and gid but this result on the error when pc login. The screen login stop and wait which this message:
> 
An error occurred while mounting /media/5001.
Keys: Press S to skip mounting or M for manual recovery
* Starting Send an event to indicate plymouth is up
* Stopping Send and event to indicate plymounth is up
*Stopping userspace bootsplash
* Starting Bridge socket events into upstart
* Stopping cold plug devices
* Stopping log initial device creation


```

UUID=e85771e4-fed0-422d-83dd-a857b6ac7ce8       /media/160      ext4    defaults        1       1
UUID=995dfb0e-119d-43db-96f5-7d2d8c854125       /media/5001     ext4    defaults,noatime,uid=1000,gid=1000      1       2
UUID=a1b72ed6-69e8-40c6-9531-9ee064bf855a       /media/5002     ext4    defaults,noatime,uid=1000,gid=1000      1       3

```

Nevertheless I tried this command via terminal:

```

gd@server:/media$ sudo mount /dev/sdd1 /media/5001 -o "uid=1000,gid=1000"
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Just can which this command:
```

sudo mount /dev/sdd1 /media/5001

```

This is my permission which all drives dismounted:

```

drwxr-xr-x  2 root root 4096 Apr 23 22:08 160
drwxr-xr-x  3 root root 4096 Apr 25 18:22 5001
drwxr-xr-x  2 root root 4096 Apr 20 21:08 5002

```

After pc start up, which this set in the /etc/fstab:

```

UUID=e85771e4-fed0-422d-83dd-a857b6ac7ce8       /media/160      ext4    defaults        1       1
UUID=995dfb0e-119d-43db-96f5-7d2d8c854125       /media/5001     ext4    defaults      1       2
UUID=a1b72ed6-69e8-40c6-9531-9ee064bf855a       /media/5002     ext4    defaults      1       3

```

The permissions it is that:

```

drwxrwxrwx  3 gd   gd   4096 Apr 25 16:04 160
drwxr-xr-x  3 root root 4096 Apr 25 18:02 5001
drwxr-xr-x  3 root root 4096 Apr 25 18:22 5002

```

---


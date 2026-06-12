---
title: "Hoary RAID1 setup problems"
date: 2005-04-11
forum: Server Platforms
---

### Post by z0mbix on 2005-04-11
Hi,

I've just finished a few installations of Hoary via "server-expert" mode, but each time I boot after the installation has successfully completed I am coming up against fsck errors. I have a mobo with 4 channels (2 x IDE, 2 x UDMA) I have 3 x identical 80GB HDD's setup as follows:

/dev/hda = Backup drive on normal IDE channel
/dev/hdc = CD-ROM drive
/dev/hde = First RAID1 drive
/dev/hdg = Second RAID1 drive

As I currently have all my backups on the drive on hda, I don't want to use that to install  grub to, so after some googling to check I could do so, I decided to install grub on /dev/hde. When the server boots up I get the following errors:

```

Booting 'Ubuntu, kernel 2.6.10-5-386'

root (hd1,0)
  Filesystem type is ext2fs, partition type 0xfd
  kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/md0 ro quiet splash
	[Linux-bzImage, setup=0x1600, size=0x1209f6]
initrd /boot/initrd.img-2.6.10-5-386
	[Linux-initrd @ 0xfbac000, 0x430000 bytes]
savedefault
boot
Uncompressing Linux... Ok, booting kernel.
autit(1113229393.158:0): initiated
Starting Ubuntu...
mdadm: /devfs/md/0 has been started with 2 drives.
  *  Mounting a tmpfs over /dev...
  	...done.
  *  Creating initial device nodes...
  	...done.
null symbol found
  *  Setting disc parameters...
  	...done.
  *  Checking root file system...
/: clean, 882/144576 files, 97697/289024 blocks
	...done.
  *  System clock wass not updated at thsi fime.
  * Cleaning up ifupdown...
  	...done.
  *  Calculating module dependencies...
  	...done.
  *  Loading modules..
  	...done.
  *  Creating device-mapper devices...
  	...done.
  *  Starting RAID devices...
mdadm: error opening /dev/md4: No such file of directory
mdadm: error opening /dev/md3: No such file of directory
mdadm: error opening /dev/md2: No such file of directory
mdadm: error opening /dev/md1: No such file of directory
	...fail!
  *  Setting up LVM Volume Groups...
  	...done.
  *  Starting Enterprise Volume Management System...
  	...done.
  *  Checking all file systems...
fsck.ext3: No such file or directory while trying to open /dev/md1
/dev/md1:
The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap of ufs or something else), then the superblock
is currupt, and you might try running e2fsck with an alternate superblock:
	e2fsck -b 8193 <device>
fsck.ext3: No such file or directory while trying to open /dev/md2
/dev/md2:
The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap of ufs or something else), then the superblock
is currupt, and you might try running e2fsck with an alternate superblock:
	e2fsck -b 8193 <device>
	fsck.ext3: No such file or directory while trying to open /dev/md3
/dev/md3:
The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap of ufs or something else), then the superblock
is currupt, and you might try running e2fsck with an alternate superblock:
	e2fsck -b 8193 <device>
	fsck.ext3: No such file or directory while trying to open /dev/md4
/dev/md4:
The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap of ufs or something else), then the superblock
is currupt, and you might try running e2fsck with an alternate superblock:
	e2fsck -b 8193 <device>
	
	...fail!
	
  *  fsck failed. Please repair manually.
  
  *  CONTROL-D will exit from this shell and continue system startup.
  
Give root password for maintenance
(or type Control-D to continue):

```

----------

I type Control-D and bootup continues normally:

----------

```

  *  Mounting local filesystems...
/dev/md1 on /usr type ext3 (rw)
/dev/md2 on /var type ext3 (rw)
/dev/md3 on /tmp type ext3 (rw)
/dev/md4 on /home type ext3 (rw)
...

``` 

My /etc/fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/md0        /               ext3    defaults,errors=remount-ro 0       1
/dev/md1        /usr            ext3    defaults        0       2
/dev/md2        /var            ext3    defaults        0       2
/dev/md3        /tmp            ext3    defaults        0       2
/dev/md4        /home           ext3    defaults        0       2
/dev/hde7       none            swap    sw              0       0
/dev/hdg7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

Is something happening in the wrong order here? I've tried moving a few things around in the boot order but always end up with the same errors. Can anybody help? Anyone seen this behaviour before?
 
Thanks alot z0mbix

---

### Post by tonym on 2005-04-12
I had a problem a little like this.  There is a known problem regarding timing of events at boot and udev devices not being created quickly enough. I got round it by adding a 5 second sleep at the beginning of the fsck script in /etc/init.d

Regards

Tony Middleton.

---

### Post by z0mbix on 2005-04-12
Thanks alot Tony, I'll try that now.

---

### Post by z0mbix on 2005-04-12
I'm still getting the msgs below so I'll have to play around to see how to fix that, but the fsck works fine now, Thanks very much.

```

  *  Starting RAID devices...
mdadm: error opening /dev/md4: No such file of directory
mdadm: error opening /dev/md3: No such file of directory
mdadm: error opening /dev/md2: No such file of directory
mdadm: error opening /dev/md1: No such file of directory
	...fail!

```

---

### Post by guid00 on 2005-06-02
hi,

I am having the same issues. Did you manage to solve the problem?

/g

---

### Post by z0mbix on 2005-06-02
I didn't but the error msgs I get do not affect anything. In the bug report, they say it will be fixed by breezy.

---

### Post by guid00 on 2005-06-02
where exactly did you make the change in the initscripts to fix the fsck issue?

/g

---

### Post by alastair on 2005-06-02
You can get rid of the "No such file of directory" warnings by "hardcoding" the device creation for udev in the file :

/etc/udev/links.conf

e.g.

```

M md0           b 9 0
M md1           b 9 1
M md2           b 9 2
M md3           b 9 3
M md4           b 9 4

```

---

### Post by guid00 on 2005-06-03
[QUOTE=alastair]/etc/udev/links.conf

e.g.

```

M md0           b 9 0
M md1           b 9 1
M md2           b 9 2
M md3           b 9 3
M md4           b 9 4

```[/QUOTE]
i tried that but it just does not work :(
any other ideas?

---

### Post by guid00 on 2005-06-03
another thing, which could be related.

Once i ignore the errormessages and press CTRL-D to continue startup,
the initscripts load some services **before** the raidarrays.

This causes havok on my system with Postfix and cron since i run /var/spool from one of the arrays.

Still no clue on how to solve the other problem tho :(

---

### Post by z0mbix on 2005-06-03
[QUOTE=guid00]where exactly did you make the change in the initscripts to fix the fsck issue?

/g[/QUOTE]

I added:

```
sleep 5
```

at the top of the file /etc/init.d/checkfs.sh

---

### Post by qd989 on 2005-06-22
[QUOTE=tonym]I had a problem a little like this.  There is a known problem regarding timing of events at boot and udev devices not being created quickly enough. I got round it by adding a 5 second sleep at the beginning of the fsck script in /etc/init.d

Regards

Tony Middleton.[/QUOTE]


Yep, that did it for me.
Still fails just after the starting RAID section, but is OK once the mounting occurs.
I had to do sleep 10 at the top of checkfs, but hey, it's done

thanks!
j

---

### Post by tonym on 2005-06-22
I've recently found a workaround for this.  I delete the config file in /etc/mdadm.  The RAID devices till come up quite happily but the error messages don't appear.

It has also fixed another problem.    I have LVM volumes on RAID1 and the LVM devices were being initialised before the RAID1.  Thus LVM detected the volume underlying the RAID1 and ran with one mirror only,  thus corrupting my partition very thoroughly.  This also went away when I deleted the config flie.

Regards

Tony.

---

### Post by alastair on 2005-06-23
That's interesting.

A few weeks ago, I installed Ubuntu on a couple of new Dell 1800 servers at work. I thought I'd do LVM on top of RAID 1 (each had 2 system disks). But this caused massive problems - after a reboot I would almost always get big filesystem corruption (e.g. /var almost empty, fsck on boot all the time etc.). I switched to straight RAID 1 (md).

I wonder if deleting the mdadm.conf would have helped?

---

### Post by tonym on 2005-06-24
[QUOTE=alastair]That's interesting.

A few weeks ago, I installed Ubuntu on a couple of new Dell 1800 servers at work. I thought I'd do LVM on top of RAID 1 (each had 2 system disks). But this caused massive problems - after a reboot I would almost always get big filesystem corruption (e.g. /var almost empty, fsck on boot all the time etc.). I switched to straight RAID 1 (md).

I wonder if deleting the mdadm.conf would have helped?[/QUOTE]
 Yes,  that's exactly the sort of problems I had. Its working fine now.

---

### Post by duren on 2007-01-26
I just ran into the same problem with Edgy. md* devices were not created so my software raid wouldn't autostart and no udev rule or entry in links.conf fixed it.

I did some poking and totally found my own solution... udev has a skeletal structure which contains a few devices that always appear to be copied. If you create your md devices in there, they will always be created in /dev !!! The structure is in /lib/udev/devices

I hope this helps someone.

---


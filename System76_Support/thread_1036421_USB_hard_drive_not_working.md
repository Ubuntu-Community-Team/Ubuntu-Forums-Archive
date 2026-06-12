---
title: "USB hard drive not working"
date: 2009-01-10
forum: System76 Support
---

### Post by Modax42 on 2009-01-10
I recently got a 500GB USB HDD for backing up my Daru 3.  Unfortunately, when I plug it in, I get this message
>  Cannot mount volume.  Unable to mount volume New Volume 


When i click on Details, I get this message

>  $LogFile indicates unclean shutdown (0,1) Failed to mount '/dev/sdb1': Operation not supported Mount is denied because NTFS is marked to be in use.  Choose an action: Choice 1: If you have windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly.  Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility.  For example type on the command line: mount -t ntf-3g /dev/sdb1 /media/New Volume -o force   Or add the option to the relevant row in the /etc/fstab file: dev/sdb1/media/New Volume ntfs-3g force 00 

When I did Choice two in the terminal, it spit out a long message

>  Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

Trying to read this just made my head spin. Anyone have any ideas?

---

### Post by drewbenn on 2009-01-10
I have an external hard drive that does this, too.
It looks, from the output, that you tried 'mount' with an invalid option.  Did you try
```
mount -t ntf-3g /dev/sdb1 /media/New Volume -o force
```
Also, ensure the directory in /media/ exists, and I would use something without a space in it, too.  You _might_ need to run mount with root privileges, too (i.e. prefix it with 'sudo'), but I'm not sure.  So, maybe:
```
sudo mkdir /media/usbhdd
sudo mount -t ntf-3g /dev/sdb1 /media/New Volume -o force
```
Also, I use "-t ntfs-3g" not "-t ntf-3g" (your output had a missing 's'). Try that, too?
One more thing, if all that doesn't work, that might help diagnose the problem, is to get the complete input and output from your terminal.  Before doing anything, run 'script', which will output everything you type into a file called 'typescript', then execute the commands that aren't working, then type 'exit', and attach the 'typescript' file to this thread.

---

### Post by tcrapper on 2009-01-10
A better solution would be to format the drive using FAT32.

run
```
sudo fdisk -l
```

To get the name of the drive, you need the partition that is "ntfs", something like /dev/sdax. You can also post the output here, and somebody can figure out which device it is for you, so you don't format the wrong drive...

Oops didn't look at the error, and it looks like your device is /dev/sdb1,but run the above command to be sure. You don't want to format the wrong drive.

If it isn't /dev/sdb1, then change it to the correct drive.

then run
```
sudo mkdosfs -F 32 /dev/sdb1
```

---

### Post by jdb on 2009-01-10
> **tcrapper said:**
> A better solution would be to format the drive using FAT32.

run
```
sudo fdisk -l
```

To get the name of the drive, you need the partition that is "ntfs", something like /dev/sdax. You can also post the output here, and somebody can figure out which device it is for you, so you don't format the wrong drive...

Oops didn't look at the error, and it looks like your device is /dev/sdb1,but run the above command to be sure. You don't want to format the wrong drive.

If it isn't /dev/sdb1, then change it to the correct drive.

then run
```
sudo mkdosfs -F 32 /dev/sdb1
```

If you use a dos partition for linux backups a lot of important file information is lost.
Things like owners, permissions, links, etc.

jdb

---

### Post by tcrapper on 2009-01-11
Yeah I guess your right, it depends what your backing up. If your just backing up personal files, like pictures, videos and stuff, then it shouldn't matter. You can always format it in a linux partition too.

```
mke2fs -j /dev/sdb1
```

Which will format it as a ext3 partition.

Oh yeah and if you use NTFS won't you loose the same information or at least some of it?

---

### Post by jdb on 2009-01-11
> **tcrapper said:**
> Yeah I guess your right, it depends what your backing up. If your just backing up personal files, like pictures, videos and stuff, then it shouldn't matter. You can always format it in a linux partition too.

```
mke2fs -j /dev/sdb1
```

Which will format it as a ext3 partition.

Oh yeah and if you use NTFS won't you loose the same information or at least some of it?

Yeah, NTFS is just a windoze "improvement" of FAT :lolflag:

jdb

---

### Post by Modax42 on 2009-01-11
Thanks guys, its working great now! :guitar: 

I tried to attach the typescript file, but the attachment manager thing told me it was an 'invalid file' for some reason.  Oh well.

---


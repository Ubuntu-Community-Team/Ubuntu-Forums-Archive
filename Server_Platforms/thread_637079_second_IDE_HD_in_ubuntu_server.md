---
title: "second IDE HD in ubuntu server"
date: 2007-12-10
forum: Server Platforms
---

### Post by macme on 2007-12-10
Question.
I add a second HD in my server ubuntu 7.04 server, IDE in second IDE connector

I want to use it for my FTP server.
I can mount it, it will make a dir and then i don't know how to go further,

Result sfdisk -l

Disk /dev/sda: 8855 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   8619    8620-  69240118+  83  Linux
/dev/sda2       8620    8854     235    1887637+   5  Extended
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5       8620+   8854     235-   1887606   82  Linux swap / Solaris

Disk /dev/sdb: 4866 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1          0+   4865    4866-  39086113+  83  Linux
/dev/sdb2          0       -       0          0    0  Empty
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty

---

### Post by bproven on 2007-12-10
From what I can tell, you just need to be able to format the new drive for Ubuntu and then add it to fstab so that it will mount on boot.  

Format the drive in ext3 - use "mkfs.ext3 /dev/<partition>" where <partition> is the partition on your device (example /dev/sdb1).  Looks like you have quite a few (1-4 on sdb - I assume /dev/sdb is your added IDE drive?). If so you probably want to format each partition if you are using them all.

Add to fstab - open /etc/fstab and add an entry which includes the partition and the mount point on each line.  You can probably take a look at what is already in there for hints on how to do it.

I can try to be more detailed if needed, but I think this will get you started.

---

### Post by macme on 2007-12-10
this is the line after i did mkfs.ext3 /dev/sdb1

/dev/sdb1  /maxtor40  ext2  suid,dev,exec  0  0

---

### Post by bproven on 2007-12-10
OK so you reformatted sdb1 and that line is what you are adding to your fstab?  Since you reformatted in ext3 change "ext2" to "ext3".  

Also I would try this line first to make sure it works:

/dev/sdb1    /maxtor40     ext3     defaults       0       1

the only real diff being the options passed in at boot "defaults" replacing your "suid,dev,exec"

options are explained here:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

When you reboot (provided you have created the /maxtor40 dir on your file system already ) it should mount at boot

---

### Post by macme on 2007-12-11
Thanks for the last help, it is working now.


My second question is i want to record my recordings also to that Maxtor40, using a dreambox sat reciever.

Mounted de /media/hdd from the dreambox, made a mount point, made in the server a user with the acces to that dir.

only when i want to record it says, inaccesable storage...

---

### Post by bproven on 2007-12-15
I don't know much about this configuration.  Maybe someone else can step in and help you with this.  Good luck...

---

### Post by macme on 2007-12-17
Thanks, it is working now.

can i add a IDE HD in the server with a lot of files on it, mounting it, without losing all the files???

---

### Post by koenn on 2007-12-17
yes. it would be the same as mounting a cd-rom  or an usb drive (with files on it) , no ?

---

### Post by macme on 2008-01-22
I want to put in the ide cable a second HD, 

first connecter is the maxtor 320Gb as slave, /dev/sdb1, second connector at the cable a samsung 320 Gb but it didn't exept it, tried as slave or master.

By jumper on master the server wants to try to boot from the master (samsung) disk.
Both slave, wil not exept

Somebody an idea?????

---


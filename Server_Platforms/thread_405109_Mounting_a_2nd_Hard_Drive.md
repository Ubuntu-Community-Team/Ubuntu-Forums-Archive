---
title: "Mounting a 2nd Hard Drive"
date: 2007-04-09
forum: Server Platforms
---

### Post by novice1 on 2007-04-09
I have set up an Edgy Server and it has two hard drives, both were detected during installtion and I selected the Primary hard drive for system boot up and installation. The server is running fine. But I can not figure out how to mount the second drive. I use both command line and Webmin to configure the Server - the Webmin Partition Managere shows both hard drive. The second hard drive has a Linux partition on it -- but I can not find the correct options using the mount command that will mount the hard drive. I want it to mount on Boot every time as well.  The "Server Documentation" is of no help and I've not found anything helpful searching on the forums.

---

### Post by quux on 2007-04-09
Hi,

You need to add an entry to /etc/fstab. A description of the file format can be found e.g. at [http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html"). To find the identifier of the partition to be mounted, "sudo fstab -l /dev/..." can be used; where ... is to be replaced with the disk device, e.g. hda, sda, ...

HTH

---

### Post by novice1 on 2007-04-09
When I type the command you suggested all I get is this:

$ /etc$ sudo fstab -|/dev/hdb
-bash: /dev/hdb: Permission denied
sudo: fstab: command not found

Thats been my frustration how on earth do I find the device ID -- I can read the contents of fstab and see how the mounts are formatted but with out a device ID I am stuck.

---

### Post by novice1 on 2007-04-09
I managed to get the drive mounted using Webmin and creating a ext3 file system and mounting at a specific mount point in the file system. I better understand the process now but I still wonder about the use of fstab as a command as it seems Steve had suggested. Maybe I just misunderstand what you meant.

---


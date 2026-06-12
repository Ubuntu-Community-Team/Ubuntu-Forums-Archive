---
title: "fs driver - Xp seeing Ext3"
date: 2008-12-09
forum: Windows
---

### Post by tadcan on 2008-12-09
So I have installed the program from [www.fs-driver.org](www.fs-driver.org) so that windows XPpro Sp3 can see my Ubuntu 8.10 /home Ext3 partition.

I have assigned it a drive letter, but windows still sees it as an unknown partition. 

Its the first time I've tried this kind of setup. Any thoughts?

---

### Post by psusi on 2008-12-09
From the FAQ on that web site:

>  The current version of Ext2 IFS only mounts volumes with an inode size of 128 like old Linux kernels have.

Some very new Linux distributions create an Ext3 file systems with inodes of 256 bytes. Ext2 IFS 1.11 is not able to access them.

Currently there is only one workaround: Please back up the files and create the Ext3 file system again. Give the mkfs.ext3 tool the -I 128 switch. Finally, restore all files with the backup. 

---

### Post by HermanAB on 2008-12-09
Here is the 21st Century solution:
Install VMware or Virtualbox, and run XP as a VM inside Ubuntu.  Then install the OpenSSH Server on the Ubuntu host, and use Filezilla from Windows to access the Ubuntu file system.

---

### Post by tadcan on 2008-12-09
Thanks. mkfs.ext3 needs to be done via the terminal and isn't availible in gparted?

@HermanAD. Your solution invovles not having a dual boot system? Thats not practical because I need to run Video editing and other intensive stuff. 

Maybe an idiots solution of making it an Ext2 partition instead!

---

### Post by psusi on 2008-12-09
Yes, you have to run it from the command line.

---

### Post by tadcan on 2008-12-10
Tried it as an Ext2 partition. Same result. :confused:

---

### Post by maybeway36 on 2008-12-10
You might want to try a different ext2 driver. This might work:
[http://sourceforge.net/projects/ext2fsd/](http://sourceforge.net/projects/ext2fsd/)

---

### Post by tadcan on 2008-12-10
Thanks. Installed it and was able to write files to the drive. So I copied over the MY Documents and settings. 

Then when I logged into ubuntu it couldn't create /home and file system check failed. 

Probably down to how I installed Ubuntu not paying attention to what was the primary and logical partition. Oh well, nothing important there. Move stuff back, start again.

I found the thread again. 8.1o doesn't work. 

[http://ubuntuforums.org/showthread.php?t=568731&highlight=dual+boot](http://ubuntuforums.org/showthread.php?t=568731&highlight=dual+boot)

---


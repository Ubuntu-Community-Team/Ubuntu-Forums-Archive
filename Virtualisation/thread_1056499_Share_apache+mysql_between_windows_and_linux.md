---
title: "Share apache+mysql between windows and linux"
date: 2009-01-31
forum: Virtualisation
---

### Post by Virtual DarKness on 2009-01-31
Well.. the post title doesn't explain very well what I mean but I'm a php developer / webmaster and what I'd like to achieve is:

- being able to read / write my sites (php files, images, ..) and emails from windows and linux so that if I edit a file using linux and then switch to windows I can just continue editing it..

- keep the linux file permissions for my files so that when I'm on linux the files will have 644 permissions and the folders 755 until I don't want to change them

This means that:
- I can't use ntfs as the partition for keep my websites/projects


On the next post I'll write 3 possible solutions I found but none of them is perfect for me. Will be a long post so that is why I'm splitting it. Thanks in advice if you'll take the time for read it (maybe you'll find some information usefull too)

bye,
Giovanni.

---

### Post by Virtual DarKness on 2009-01-31
Possible solutions

1) install, on windows, vmware server 1 with a virtual disk for an ubuntu install and a second disk that points to a raw partition. The raw partition would be the linux partition used for linux data (like the home partition, not the root one). In this way you can have apache + mysql running on the vmware server machine that reads the file from the real linux partition when you are on windows, and when you are in linux you just run it as usual. For editing files from windows you can then set up a sshfs connection using dokan sshfs ([http://dokan-dev.net/en/](http://dokan-dev.net/en/)) that is very fast as you are using the bridget network adapter of vmware and also lets you change the linux folders and file permissions from windows.

1b) instead of vmware you can use andLinux/coLinux but it doesn't supports 64bit ..

2) use ext2fsd ([http://ext2fsd.sourceforge.net/](http://ext2fsd.sourceforge.net/)) for mount your data ext3 partition under windows .. you can't set the files permissions from windows but it won't overwrite your premissions and will inherit new file permissions according to the current folder permissions.

3) using vmware server you can make a disk image you share between windows and linux that contains your websites/project files.. then on windows you mount the disk or the folders you need using samba .. and on linux using nfs .. 



Things that I don't like / doesn't works as I'd like for each possible solution:

1) - vmware server v2 doesn't allow you to use physical/raw disks anymore :(
- vmware server v1 says that is not safe to use a physical/raw disk
- changes to the linux partition would require you to change the vmware image too
- not sure about how much reliable dokan sshfs is

2) - you have to use apache and mysql compiled for windows
 - would be a problem to use mysql server as probably the windows and linux version wont match so there could be database data corruption
- don't know how much reliable ext2fsd is and the project doesn't have any svn commit since sep. 2008.

3) - don't like the idea of have to move my projects inside a vmware disk image
- at this point would like to use virtualbox instead of vmware when there will be the OSE binaries for windows with a GUI (without the need to compile the OSE version for windows)
- not sure if I can use a raw disk image so that maybe I can just mount it under linux instead of using it as a NFS share.


ok.. so at this point.. what do you suggest? which one could be the best solution and why / how would you improve it? do you share your projects between windows and linux too and how do you manage it?

thanks for reading.

bye,
Giovanni.

---

### Post by jon23d on 2009-02-01
I just share /var/www if I want to work in a windows vm

---

### Post by Virtual DarKness on 2009-02-01
> **jon23d said:**
> I just share /var/www if I want to work in a windows vm

hi jon23d,
I don't want to have a windows vm.. I want windows to run on real hardware and then have linux run in a vm inside windows.. And then I want to be able to reboot to linux on real hardware and have the same environment (server + project files).

Thanks.

Giovanni.

---

### Post by inject0r on 2010-03-14
hi Giovanni,

I'm having the same problem too, have you find any useful solutions?

thanks
Tariq

---


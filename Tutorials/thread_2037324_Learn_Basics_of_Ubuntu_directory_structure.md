---
title: "Learn Basics of Ubuntu directory structure"
date: 2012-08-04
forum: Tutorials
---

### Post by vipulkumar7 on 2012-08-04
[LEFT][SIZE=4]
**[SIZE=2]Hellow my name is Vipul kumar. And i am going to tell you about Basics of Ubuntu Linux, for new comers .1st let me tell you, you shud know about Directory structure in ubuntu linux.[/SIZE]**

[/SIZE]**In Ubuntu Linux, this is the basic format**
**> *# /Folder1or Directory/subfolder or sub-Directory/file.txt***
[SIZE=4]
[SIZE=2]**it's something like that in my ubuntu 12.04**

[/SIZE][/SIZE]
[SIZE=4]
[/SIZE]**The Main Directories are in Ubuntu Linux **


[ATTACH]222233[/ATTACH]


**1. / – Root**
**2. /bin – User Binaries**
**3. /sbin – System Binaries**
**4. /etc – Configuration Files**
**5. /dev – Device Files**
**6. /proc – Process Information**
**7. /var – Variable Files**
**8. /tmp – Temporary Files**
**9. /usr – User Programs**
**10. /home – Home Directories**
**11. /boot – Boot Loader Files**
**12. /lib – System Libraries**
**13. /opt – Optional add-on Applications**
**14. /mnt – Mount Directory**
**15. /media – Removable Media Devices**
**16. /srv – Service Data**

**Let me explain each of them :)**

**1. / – Root**

**The root directory. The starting point of your directory  structure. This is where the Linux system begins. Every other file and  directory on your system is under the root directory. Usually the root  directory contains only subdirectories, so it’s a bad idea to store  single files directly under root.Only root user has write privilege  under this directory.Please note that /root is root user’s home  directory, which is not same as /** .

**you can go inside root directory via**

[B][I]# cd /

#ls

[/I][/B][ATTACH]222232[/ATTACH]


**2. /bin – User Binaries, /usr/bin**

 **These two directories contain a lot of programs (binaries,  hence the directory’s name) for the system. Common linux commands you  need to use in single-user modes are located under this directory.The  /bin directory contains the most important programs that the system  needs to operate, such as the shells, ls, grep, and other essential  things For example: ps, ls, ping, grep, cp. /usr/bin in turn contains  applications for the system’s users. However, in some cases it really  doesn’t make much difference if you put the program in /bin or /usr/bin.**
 ****
**> # cd /usr/bin**
****
 **> # ls**


**#####################**

**3. /sbin – System Binaries**

 **Most system administration programs are stored in these  directories. In many cases you must run these programs as the root  user.For example: iptables, reboot, fdisk, ifconfig, swapon. It also  contains binary executables you can check by**

  **> # cd /sbin**
   ****
**> # ls**


##################

**4. /etc – Configuration Files**[INDENT] 
[/INDENT][B]The configuration files for the Linux system.It contains  configuration files required by all programs Most of these files are  text files and can be edited by hand. Some interesting
 stuff in this directory:[/B]
****
**> # cd /etc/**
  ****
**> # ls**


#######################


**5. /dev – Device Files**

 **The devices that are available to a Linux system. Remember  that in Linux, devices are treated like files and you can read and write  devices like they were files. For example, */dev/fd0* is your first floppy drive, */dev/cdrom*  is your CD drive, /dev/hda is the first IDE hard drive, and so on. All  the devices that a Linux kernel can understand are located under */dev*,  and that’s why it contains hundreds of entries.These include terminal  devices, usb, or any device attached to the system.Example */dev/tty1, /dev/usbmon0***
 
**> # cd /dev**
****
 **> # ls**
****
##################

**6. /proc – Process Information**

 **This is a special directory. Well, actually */proc *is  just a virtual directory, because it doesn’t exist at all! It contains  some info about the kernel itself. There’s a bunch of numbered entries  that correspond to all processes running on the system, and there are  also named entries that permit access to the current configuration of  the system. Many of these entries can be viewed.by *#cd* /proc and then type *#ls*This  is a pseudo filesystem contains information about running process. For  example: /proc/{pid} directory contains information about the process  with that particular pid.Last but not least it Contains information  about system process.**
 ****
**> # cd /proc/**
****
 **> # ls**

#########################


**7. /var – Variable Files**

 **This directory contains variable data that changes constantly when the system is running.**

 **> # cd /var/**

**> # ls**


**########################**

**8. /tmp – Temporary Files**

 **Programs can write their temporary files here**.
 ****
**> # cd /tmp**

**> # ls**

#########################

**9. /usr – User Programs**

 **This directory contains user applications and a variety of other  things for them, like their source codes, and pictures, docs, or config  files they use. */usr* is the largest directory on a Linux system, and some people like to have it on a separate partition. Some interesting stuff in */usr***


**> #cd /usr**
 ****
**> # ls**

####################3

**10. /home – Home Directories**

** [B]This is where users keep their personal files. Every user has their own directory under */home*,  and usually it’s the only place where normal users are allowed to write  files. You can configure a Linux system so that normal users can’t even  list the contents of other users’ home directories. This means that if  your family members have their own user accounts on your Linux system,  they won’t see all the w4r3z you keep in your home directory. [IMG]http://s1.wp.com/wp-includes/images/smilies/icon_wink.gif?m=1129645325g[/IMG] Or you  Porn stuff hheeh [IMG]http://s0.wp.com/wp-includes/images/smilies/icon_biggrin.gif?m=1129645325g[/IMG]  **
 ****
> # cd /home/
 ****
> # ls
[/B]

########################

**11. /boot – Boot Loader Files**[B][INDENT] 
[/INDENT] **As the name suggests, this is the place where Linux keeps  information that it needs when booting up. For example, this is where  the Linux kernel is kept. If you list the contents of */boot*, you’ll see a file called vmlinuz – that’s the kernel.Kernel initrd, vmlinux, grub files are located under */boot* For example: initrd.img-2.6.32-24-generic, vmlinuz-2.6.32-24-generic **
 ****
> # cd /boot/
 ****
> # ls
[/B]
#########################

**[B]12. /lib – System Libraries**[/B]
****
[B] The shared libraries for programs that are dynamically linked. The shared libraries [B]are similar to DLL’s on Winblows 
[/B]


**#######################**

**13. /opt – Optional add-on Applications**
 
** [B]opt stands for optional.Contains add-on applications from  individual vendors.add-on applications should be installed under either  /opt/ or /opt/ sub-directory**
[/B]


#####################


**14. /mnt – Mount Directory**
[B] 
**Temporary mount directory where sysadmins can mount  filesystems.This directory is used for mount points. The different  physical storage devices (like the hard disk drives, floppies, CD-ROM’s)  must be attached to some directory in the file system tree before they  can be accessed. This attaching is called mounting, and the directory  where the device is attached is called the mount point.The /mnt  directory contains mount points for different devices, like* /mnt/*floppy for the floppy drive, */mnt/cdrom *for the CD-ROM, and so on. However, you’re not forced to use the */mnt*  directory for this purpose, you can use whatever directory you wish.  Actually in some distros, like Debian and SuSE, the default is to use */floppy* and */cdrom* as mount points instead of directories under */mnt***
 ****
> # cd/mnt/
****
 > # ls


#####################

**15. /media – Removable Media Devices**

** [B]Temporary mount directory for removable devices.For examples,  /media/cdrom for CD-ROM; /media/floppy for floppy drives;  /media/cdrecorder for CD writer**
 ****
> # cd /media/
 ****
> # ls 
[/B]


########################



**16./srv – Service Data**

** [B]srv stands for service.Contains server specific services related data.For example, /srv/cvs contains CVS related data.**
 ****
> # cd /srv/
 ****
> # ls
[/B]
[/B]
[/B]

**[B]What next?**


[B] If you’re completely new to Ubuntu Linux, you might want to learn some  commands for moving around in the file system, viewing text files, or  manipulating the files. In that case I suggest you take a look at my,   new articles coming at my  Linux command line section [IMG]http://s0.wp.com/wp-includes/images/smilies/icon_smile.gif?m=1129645325g[/IMG] ;) sTAY TuNe
[/B][/B]
:P bbye :)









[/LEFT]

---


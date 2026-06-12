---
title: "Installing VMware tools in VMplayer"
date: 2013-08-05
forum: Virtualisation
---

### Post by physman2 on 2013-08-05
I'm following these instructions: 
[http://www.vmware.com/support/ws5/doc/ws_newguest_tools_linux.html](http://www.vmware.com/support/ws5/doc/ws_newguest_tools_linux.html)
and am '[Installing VMware Tools from the Command Line with the Tar Installer]("http://www.vmware.com/support/ws5/doc/ws_newguest_tools_linux.html#wp1118025")'.

[COLOR=#333333][FONT=monospace]When I did 
[/FONT][/COLOR][COLOR=#333333][FONT=monospace]mount /dev/cdrom /mnt/cdrom
it said that there is no such directory as /mnt/cdrom so I cd into /mnt/ and mkdir cdrom.
then the 
[/FONT][/COLOR][COLOR=#333333][FONT=monospace]mount /dev/cdrom /mnt/cdrom
after cd /tmp
in the 
[/FONT][/COLOR][COLOR=#333333][FONT=monospace]tar zxf /mnt/cdrom/VMwareTools-5.0.0-<xxxx>.tar.gz
[/FONT][/COLOR][COLOR=#333333][FONT=monospace]step, it says "[/FONT][/COLOR][COLOR=#333333][FONT=Arial]Where[/FONT][/COLOR] <xxxx> [COLOR=#333333][FONT=Arial]is the build/revision number of the VMware Workstation release."
[/FONT][/COLOR][COLOR=#333333][FONT=monospace]The problem is, i'm using VMplayer, not VMware workstation. What should I do?
The instructions here: [/FONT][/COLOR][http://www.vmware.com/pdf/vmware-tools-installation-configuration.pdf](http://www.vmware.com/pdf/vmware-tools-installation-configuration.pdf)
[COLOR=#333333][FONT=monospace]say to run the command
[/FONT][/COLOR]ls (mount-point)
[COLOR=#333333][FONT=monospace]but I tried to do ls /mnt/cdrom and also tried ls /media/username/Lubuntu\ 13.04\ i386
and it said Input/output error.
Any idea what is wrong?[/FONT][/COLOR]

---

### Post by vamped on 2013-08-05
> **physman2 said:**
> I'm following these instructions: 
it said that there is no such directory as /mnt/cdrom so I cd into /mnt/ and mkdir cdrom.


You did not follow the instructions, but instead did your own thing. It did not say to create your own directory /mnt/cdrom, but said rather that if it didn't exist to modify the command.


The instructions > item 3 > said, "Some Linux distributions use different device names or organize the /dev directory differently. If your CD-ROM drive is not /dev/cdrom or if the mount point for a CD-ROM is not /mnt/cdrom, you must modify the following commands to reflect the conventions used by your distribution."

On my system (Kubuntu 13.04), /dev/cdrom is a symlink to /dev/sr0 (so /dev/sr0 is the dvd-player / cd-player)
On my system then, I could use either /dev/cdrom or /dev/sr0.

On your system, look in your /dev directory and find your cdrom. It could be called dvdrw, dvd, cdrw, cdrom, or sr0. Once you have found it, modify the commands in the instructions, substituting your device name for /dev/cdrom.

---

### Post by physman2 on 2013-08-05
> **vamped said:**
> You did not follow the instructions, but instead did your own thing. It did not say to create your own directory /mnt/cdrom, but said rather that if it didn't exist to modify the command.


The instructions > item 3 > said, "Some Linux distributions use different device names or organize the /dev directory differently. If your CD-ROM drive is not /dev/cdrom or if the mount point for a CD-ROM is not /mnt/cdrom, you must modify the following commands to reflect the conventions used by your distribution."

On my system (Kubuntu 13.04), /dev/cdrom is a symlink to /dev/sr0 (so /dev/sr0 is the dvd-player / cd-player)
On my system then, I could use either /dev/cdrom or /dev/sr0.

On your system, look in your /dev directory and find your cdrom. It could be called dvdrw, dvd, cdrw, cdrom, or sr0. Once you have found it, modify the commands in the instructions, substituting your device name for /dev/cdrom.

Right, but when I did the command 
mount
it said '/dev/sr0 on /media/username/Lubuntu 13.04 i386 type iso9660'
but when I did 
ls /media/username/Lubuntu\ 13.04\ i386
it gives an input/output error

---

### Post by vamped on 2013-08-05
It's difficult to know what's going on without further information. Issue these commands and copy-paste the actual output (wrapped in code tags)
```
mount
ls /media
ls /media/username/Lubuntu*
ls /mnt
```

---

### Post by codemaniac on 2013-08-07
*Thread moved to **Virtualisation**.*

---


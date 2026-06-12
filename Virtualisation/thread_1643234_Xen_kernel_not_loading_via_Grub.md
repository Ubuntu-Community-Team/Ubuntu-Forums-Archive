---
title: "Xen kernel not loading via Grub"
date: 2010-12-11
forum: Virtualisation
---

### Post by sawozny on 2010-12-11
Greetings Gurus!

I've loaded a machine with 10.10 server amd64 installing only the core system and OpenSSH server.  I've been following the instructions at [https://help.ubuntu.com/community/Xen#Maverick%20Notes%20(Xen%204.0.1%20pvops%20on%20Ubuntu%2010.10](https://help.ubuntu.com/community/Xen#Maverick%20Notes%20(Xen%204.0.1%20pvops%20on%20Ubuntu%2010.10)) which appear to be pretty new and had some hiccups with the make world which was resolved by installing additional modules and changing one of the git lines regarding local or remote branches.  So the make world and sudo make install steps appear to run successfully and now I need to change grub to boot the Xen kernel.

The instructions say to add the following to 40_custom (with my fs-uuid) and sudo update-grub:

menuentry "Xen 4.0  2.6.32.25 pvops" {
insmod part_msdos
insmod ext2
set root=(hd0,msdos1)
search --no-floppy --fs-uuid --set 294e6dee-238e-42c2-814f-fb47aaa45571
multiboot /boot/xen.gz
module /boot/vmlinuz-2.6.32.25 root=/dev/sda1
module /boot/initrd-2.6.32.25.img
}

Right out of the gate, I worry about the success of the menuentry due to the fact that the module lines refer to files that don't exist.  Here's my /boot directory:

sawozny@xen-host:/boot$ ls -la
total 37150
drwxr-xr-x  4 root root     1024 2010-12-11 12:12 .
drwxr-xr-x 22 root root     4096 2010-12-11 10:58 ..
-rw-r--r--  1 root root   700570 2010-10-16 21:11 abi-2.6.35-22-server
-rw-r--r--  1 root root    69063 2010-12-11 14:33 config-2.6.32.26
-rw-r--r--  1 root root   122712 2010-10-16 21:11 config-2.6.35-22-server
drwxr-xr-x  3 root root     4096 2010-12-11 14:37 grub
-rw-r--r--  1 root root 11746215 2010-12-11 10:26 initrd.img-2.6.35-22-server
drwxr-xr-x  2 root root    12288 2010-12-11 09:13 lost+found
-rw-r--r--  1 root root   165084 2010-09-24 14:16 memtest86+.bin
-rw-r--r--  1 root root   167264 2010-09-24 14:16 memtest86+_multiboot.bin
-rw-r--r--  1 root root  2375083 2010-12-11 14:33 System.map-2.6.32.26
-rw-r--r--  1 root root  2365429 2010-10-16 21:11 System.map-2.6.35-22-server
-rw-r--r--  1 root root     1335 2010-10-16 21:14 vmcoreinfo-2.6.35-22-server
-rw-r--r--  1 root root  4684000 2010-12-11 14:33 vmlinuz-2.6.32.26
-rw-r--r--  1 root root  4388496 2010-10-16 21:11 vmlinuz-2.6.35-22-server
-rw-r--r--  1 root root   679132 2010-12-11 11:28 xen-4.0.1.gz
lrwxrwxrwx  1 root root       12 2010-12-11 12:11 xen-4.0.gz -> xen-4.0.1.gz
lrwxrwxrwx  1 root root       12 2010-12-11 12:11 xen-4.gz -> xen-4.0.1.gz
lrwxrwxrwx  1 root root       12 2010-12-11 12:11 xen.gz -> xen-4.0.1.gz
-rw-r--r--  1 root root 10388082 2010-12-11 11:28 xen-syms-4.0.1
sawozny@xen-host:/boot$ 

I get 10 new boot entries right after my original default entries that result in either an error or a reboot.  Here they are:

- Ubuntu, GNU/Linux, with 2.6.32.26 and XEN syms-4.0.1
- Ubuntu, GNU/Linux, with 2.6.32.26 and XEN syms-4.0.1 (recovery mode)
- Ubuntu, GNU/Linux, with 2.6.32.26 and XEN 4
- Ubuntu, GNU/Linux, with 2.6.32.26 and XEN 4 (recovery mode)
- Ubuntu, GNU/Linux, with 2.6.32.26 and XEN 4.0
- Ubuntu, GNU/Linux, with 2.6.32.26 and XEN 4.0 (recovery mode)
- Ubuntu, GNU/Linux, with 2.6.32.26 and XEN 4.0.1
- Ubuntu, GNU/Linux, with 2.6.32.26 and XEN 4.0.1 (recovery mode)
- Ubuntu, GNU/Linux, with 2.6.32.26 and XEN xen
- Ubuntu, GNU/Linux, with 2.6.32.26 and XEN xen (recovery mode)

I'm assuming these arrived because of the new files and symlinks update-grub found in my /boot directory.  The update-grub ALSO doesn't run cleanly which is probably part of why these non-functional grub entries exist.

Here are the results of the update-grub with the errors that make me nervous:

sawozny@xen-host:~$ sudo update-grub
[sudo] password for sawozny: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-server
Found initrd image: /boot/initrd.img-2.6.35-22-server
Found linux image: /boot/vmlinuz-2.6.32.26
dpkg: version '/boot/xen.gz' has bad syntax: invalid character in version number
Found linux image: /boot/vmlinuz-2.6.32.26
dpkg: version '/boot/xen.gz' has bad syntax: invalid character in version number
Found linux image: /boot/vmlinuz-2.6.32.26
dpkg: version '/boot/xen.gz' has bad syntax: invalid character in version number
Found linux image: /boot/vmlinuz-2.6.32.26
dpkg: version '/boot/xen.gz' has bad syntax: invalid character in version number
Found linux image: /boot/vmlinuz-2.6.32.26
Found linux image: /boot/vmlinuz-2.6.32.26
Found memtest86+ image: /memtest86+.bin
done
sawozny@xen-host:~$ 

So, I decided to press on with the instructions and install EXT4 support with the following commands:

- make linux-2.6-pvops-config CONFIGMODE=menuconfig #where I went into the menus and added any EXT4 module I could find
- make linux-2.6-pvops-build
- sudo make linux-2.6-pvops-install

Then I ran another sudo update-grub and rebooted, trying the custom menu entry.  When I do, this is what I get:

- error: couldn't open file.
- error: you need to load the multiboot kernel first (this line appears twice)

Back to my earlier point, I tried to modify the lines added to 40_custom to match files that actually exist in my boot directory, but after another sudo update-grub, the error message on boot is the same.

If anyone has any idea what's gone wrong here, I'd appreciate any assistance you can offer.  I don't mind doing the research, but I can't find a good resource on modifying grub to boot Xen kernels.  If anyone knows of any, I'd appreciate being pointed in the right direction.  These instructions, as published in the Ubuntu community documentation, are pretty new so Google hasn't been much of a help.

Thanks in advance for any and all suggestions,

Scott

---

### Post by mensch0815 on 2010-12-16
Hi Scott,

since monday I'm trying to instal xen on ubuntu 10.10 either.
I've the kernel up and running, but without X up to now.

Regarding your problem:
are you sure that you have set all parameters in etc/grub.d appropriate?
note that you have to set the initrd to an existing one, as it is not build within the makefiles. maybe that's the problem.
here are my settings, if you want, I can post you the grub.cfg part as well.

```
menuentry "Xen 4.0  2.6.32.26 pvops" {
insmod part_msdos
insmod ext2
set root=(hd0,msdos1)
search --no-floppy --fs-uuid --set 3eb65281-f30f-42c3-90c1-6bd9c98b01c0
multiboot /boot/xen.gz
module /boot/vmlinuz-2.6.32.26 root=/dev/sda1
module /boot/initrd.img-2.6.32-26-generic-pae
}

```

when running update-grub I get the same errors, don't look like a big issue as my kernel is booting.

hope that helps.

---

### Post by cibrahim on 2013-03-29
Hi there,

I'm in trouble with an issue that looks like yours, namely : I have an "[COLOR=#444444][FONT=Tahoma]error : couldn't open file" error message when lauchning Xen 4.1-amd64 from grub.[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri][FONT=Tahoma]First of all, this is my configuration :[/FONT][/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri][FONT=Tahoma]Ubuntun 12.10, installed in windows 7[/FONT][/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri][FONT=Tahoma]
[/FONT][/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri][FONT=Tahoma]Here is my issues :[/FONT][/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri][FONT=Tahoma]I followed, of course, a number of tutorials, and came to the following point a installing Xen[/FONT][/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri][FONT=Tahoma]
[/FONT][/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri][FONT=Tahoma]I have the xen-4.1-amd64.gz archive in /boot[/FONT][/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri][FONT=Tahoma]
[/FONT][/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri][FONT=Tahoma]Here is what I have in /boot/grub/grub.cfg :[/FONT][/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri][FONT=Tahoma]
[/FONT][/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri][FONT=Arial][SIZE=2]### BEGIN /etc/grub.d/20_linux_xen ###[/SIZE][/FONT]
[FONT=Arial][SIZE=2]submenu "Xen 4.1-amd64" {[/SIZE][/FONT]
[FONT=Arial][SIZE=2]menuentry 'Ubuntu GNU/Linux, avec Xen 4.1-amd64 et Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os --class xen {[/SIZE][/FONT]
[FONT=Arial][SIZE=2]    insmod part_msdos[/SIZE][/FONT]
[FONT=Arial][SIZE=2]    insmod ntfs[/SIZE][/FONT]
[FONT=Arial][SIZE=2]    set root='(hd0,msdos3)'[/SIZE][/FONT]
[FONT=Arial][SIZE=2]    search --no-floppy --fs-uuid --set=root F282A3B682A37DAB[/SIZE][/FONT]
[FONT=Arial][SIZE=2]    echo    'Chargement de Xen 4.1-amd64 ...'[/SIZE][/FONT]
[FONT=Arial][SIZE=2]    multiboot    /boot/xen-4.1-amd64.gz placeholder  [/SIZE][/FONT]
[FONT=Arial][SIZE=2]    echo    'Chargement de Linux 3.2.0-23-generic ...'[/SIZE][/FONT]
[FONT=Arial][SIZE=2]    module    /boot/vmlinuz-3.2.0-39-generic placeholder root=/dev/mapper/control ro  [/SIZE][/FONT]
[FONT=Arial][SIZE=2]    echo    'Chargement du disque mémoire initial ...'[/SIZE][/FONT]
[FONT=Arial][SIZE=2]    module    /boot/initrd.img-3.2.0-39-generic[/SIZE][/FONT]
[FONT=Arial][SIZE=2]}[/SIZE][/FONT]
[FONT=Arial][SIZE=2]menuentry 'Ubuntu GNU/Linux, avec Xen 4.1-amd64 et Linux 3.2.0-23-generic (mode de dépannage)' --class ubuntu --class gnu-linux --class gnu --class os --class xen {[/SIZE][/FONT]
[FONT=Arial][SIZE=2]    insmod part_msdos[/SIZE][/FONT]
[FONT=Arial][SIZE=2]    insmod ntfs[/SIZE][/FONT]
[FONT=Arial][SIZE=2]    set root='(hd0,msdos3)'[/SIZE][/FONT]
[FONT=Arial][SIZE=2]    search --no-floppy --fs-uuid --set=root F282A3B682A37DAB[/SIZE][/FONT]
[FONT=Arial][SIZE=2]    echo    'Chargement de Xen 4.1-amd64 ...'[/SIZE][/FONT]
[FONT=Arial][SIZE=2]    multiboot    /boot/xen-4.1-amd64.gz placeholder  [/SIZE][/FONT]
[FONT=Arial][SIZE=2]    echo    'Chargement de Linux 3.2.0-23-generic ...'[/SIZE][/FONT]
[FONT=Arial][SIZE=2]    module    /boot/vmlinuz-3.2.0-39-generic placeholder root=/dev/mapper/control ro single[/SIZE][/FONT]
[FONT=Arial][SIZE=2]    echo    'Chargement du disque mémoire initial ...'[/SIZE][/FONT]
[FONT=Arial][SIZE=2]    module    /boot/initrd.img-3.2.0-39-generic[/SIZE][/FONT]
[FONT=Arial][SIZE=2]}[/SIZE][/FONT]
[FONT=Arial][SIZE=2]}[/SIZE][/FONT]
[FONT=Arial][SIZE=2]### END /etc/grub.d/20_linux_xen ###[/SIZE][/FONT]
[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri][FONT=Tahoma]
[/FONT][/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri][FONT=Tahoma][SIZE=3]And so, when grub starts, I choose "Xen 4.1-amd64",[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri][FONT=Tahoma][SIZE=3] then[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri][FONT=Tahoma][SIZE=3] "Ubuntu GNU/Linux, avec Xen 4.1-amd64 et Linux 3.2.0-23-generic"[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri][FONT=Tahoma][SIZE=3]
[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri][FONT=Tahoma][SIZE=3]after which I got these 3 beautiful messages :[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri][FONT=Tahoma][SIZE=3]Xen 4.1-amd64[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri][FONT=Tahoma][SIZE=3]error : couldn't open file[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri][FONT=Tahoma][SIZE=3]Linux-generic...[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri][FONT=Tahoma][SIZE=3]you need to load the multiboot kernel first[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri][FONT=Tahoma][SIZE=3]Mem init...[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri][FONT=Tahoma][SIZE=3]you need to load the multiboot kernel first[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri][FONT=Tahoma][SIZE=3]
[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri][FONT=Tahoma][SIZE=3]I guess the 2 last messages are a consequence of the first, but I can't figure why grub couldn't open Xen 4.1-amd64, that is to say /boot/xen-4.1-amd64.gz[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri][FONT=Tahoma][SIZE=3]
[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri][FONT=Tahoma][SIZE=3]I'd be hugely thankful if someone could help me in any way ! Thanks in advance ![/SIZE][/FONT][/FONT][/COLOR]

---

### Post by tgalati4 on 2013-03-29
So, if I understand your issue, you are trying to launch a virtualized environment inside a virtualized environment?  What virtual machine is running Ubuntu 12.10 inside Windows7?  Does that virtual machine allow a virtual machine OS as a guest?

How about taking bare hardware--with no other operating system, and loading Xen?

This is an old  thread (2010) and is likely to be closed.

---

### Post by wildmanne39 on 2013-03-30
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---


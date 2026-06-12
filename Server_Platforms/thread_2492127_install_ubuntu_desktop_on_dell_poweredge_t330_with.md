---
title: "install ubuntu desktop on dell poweredge t330 with raid"
date: 2023-10-31
forum: Server Platforms
---

### Post by tweky on 2023-10-31
[COLOR=#202124][FONT=arial]I can't install ubuntu on my server, I go into the lifecycle controller, I do everything I need to do, but I can't install ubuntu after.....

[/FONT][/COLOR][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292988&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292986&stc=1[/IMG]
[COLOR=#202124][FONT=arial]I can't install ubuntu on my server, I go into the lifecycle controller, I do everything I need to do, but I can't install ubuntu after.....[/FONT][/COLOR]

---

### Post by MAFoElffen on 2023-10-31
I have and have had a whole lot of DELL PE EC2 server hardware...

Which PERC RAID Controller do you have? PERC S130, PERC H330, PERC H730, or PERC H830?

A few things... While installing choose "Safe Graphics" (nomodeset). See if that starts the installer with graphics. 

If that doesn't, then add this to the Linux boot line in the Grub2 menu: 
```

video=uvesafb:1280x1024-24@60,mtrr:3,ywrap,noblank

```
If you need instructions for doing that, and booting with that just ask...

If it does install, it will work if you run X11 (xorg), but you need to be using driver package ''xserver-xorg-video-mga", which is not a default installed package. 

It has an iGPU of Matrox G200, with 1280x1024x60 as it's highest resolution.

It's easiest to install after the installation is through, and select "Continue Exploring", open a terminal to chroot into the same target mount that it used during the install, and installing that driver into the installed system.

---

### Post by MAFoElffen on 2023-10-31
Just going ahead and posting it... After the install and returning to the desktop of the Installer Live Environment, start a terminal
```

sudo su
mount --make-private --rbind /dev  /target/dev
mount --make-private --rbind /proc /target/proc
mount --make-private --rbind /sys  /target/sys
mount --make-private --rbind /run  /target/run
chroot /target /usr/bin/env bash --login
apt install -y xserver-xorg-video-mga
X -configure
cp /root/xorg.conf.new /etc/X11/xorg.conf.d/00-matrox.conf
exit
umount /target
exit

```

---

### Post by tweky on 2023-11-03
thanks :D

---

### Post by MAFoElffen on 2023-11-14
How did that go?

If this is "Solved"... If so, you can select the "Thread Tools" link to mark your thread as "Solved". That helps other to find what worked for you with their similar problems.

---


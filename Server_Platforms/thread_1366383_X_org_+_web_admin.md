---
title: "X org + web admin"
date: 2009-12-28
forum: Server Platforms
---

### Post by ndnd on 2009-12-28
Hello all,
I am fairly new to linux (as an administrator). I have recently installed the Ubuntu Server edition (9.10) and is working perfectly fine. The main purpose is to have a low overhead system for a specific GUI based software. 

I need to install X org or something similar that allows me to run GUI based softwares but keeping the usage of system resources to minimal. 

From this link 

[http://ubuntuforums.org/showthread.php?t=225005]("http://ubuntuforums.org/showthread.php?t=225005")

> 
My observations 
1) X org is the way to go:
Minimal system resources and GUI is enabled
2) Login managers are helpful but not required (apart from the default) 
3) X windows session has to be "enabled" by the user or in a script at login because it **does not** start when user logs in correct ?


Any other recommendations in terms of packages for installation that can help in remote administration I saw a link for 

[http://www.webmin.com/]("http://www.webmin.com/")
Anything  better or some sorts of comparisions? I will have a high turnover of  user accounts and giving them disk space as well as  a shared space. 



Your thoughts suggestions are appreciated

---

### Post by ndnd on 2009-12-28
Hey guys,
Just following up :)...It is a bit urgent for me :)

I have tried to install the Xorg 

when i give startX (remotely through SSH)
I get the following error 

> X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux tango 2.6.31-14-server #48-Ubuntu SMP Fri Oct 16 15:07:34 UTC 2009 x86_64
Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.31-14-server root=UUID=9243e49d-9803-42ee-8406-e0fb27f4df7e ro quiet splash
Build Date: 26 October 2009  05:19:56PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Dec 28 14:25:41 2009
(==) Using default built-in configuration (30 lines)
(EE) open /dev/fb0: No such file or directory
(EE) MGA(0): Static buffer allocation failed, not initializing the DRI
(EE) MGA(0): Need at least 15360 kB video memory at this resolution, bit depth
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server




Not sure if I am missign packages...is there something better to install here. All I need is to  be able to open GUI based package 

My understanding is Gnome or KDE are intensive GUI apps and therefore would not like to install them.

---


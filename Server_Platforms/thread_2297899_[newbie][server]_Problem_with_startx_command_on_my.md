---
title: "[newbie][server] Problem with startx command on my server"
date: 2015-10-07
forum: Server Platforms
---

### Post by Martin_Kadlcek on 2015-10-07
Hello everyone!
Today, I installed on my own server Ubuntu Server, 14.04, whose I updated via. commands "apt-get update" and "apt-get upgrade". Everything worked fine. 
After that, I installed xubuntu-desktop GUI, but when I wrote command "startx", I will get some error message, whose is on next lines.

> 
[FONT=Monaco]root@mcserver:/home/martin# startx
[/FONT]
[FONT=Monaco]X.Org X Server 1.15.1[/FONT]
[FONT=Monaco]Release Date: 2014-04-13[/FONT]
[FONT=Monaco]X Protocol Version 11, Revision 0[/FONT]
[FONT=Monaco]Build Operating System: Linux 3.2.0-75-generic i686 Ubuntu[/FONT]
[FONT=Monaco]Current Operating System: Linux mcserver 3.16.0-30-generic #40~14.04.1-Ubuntu SMP Thu Jan 15 17:45:15 UTC 2015 i686[/FONT]
[FONT=Monaco]Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-30-generic root=UUID=bda58454-f30b-4669-bccd-473dc1bb20dd ro[/FONT]
[FONT=Monaco]Build Date: 12 February 2015  02:49:46PM[/FONT]
[FONT=Monaco]xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) [/FONT]
[FONT=Monaco]Current version of pixman: 0.30.2[/FONT]
[FONT=Monaco]    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)[/FONT]
[FONT=Monaco]    to make sure that you have the latest version.[/FONT]
[FONT=Monaco]Markers: (--) probed, (**) from config file, (==) default setting,[/FONT]
[FONT=Monaco]    (++) from command line, (!!) notice, (II) informational,[/FONT]
[FONT=Monaco]    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.[/FONT]
[FONT=Monaco](==) Log file: "/var/log/Xorg.1.log", Time: Wed Oct  7 15:53:28 2015[/FONT]
[FONT=Monaco](==) Using system config directory "/usr/share/X11/xorg.conf.d"[/FONT]
[FONT=Monaco]Initializing built-in extension Generic Event Extension[/FONT]
[FONT=Monaco]Initializing built-in extension SHAPE[/FONT]
[FONT=Monaco]Initializing built-in extension MIT-SHM[/FONT]
[FONT=Monaco]Initializing built-in extension XInputExtension[/FONT]
[FONT=Monaco]Initializing built-in extension XTEST[/FONT]
[FONT=Monaco]Initializing built-in extension BIG-REQUESTS[/FONT]
[FONT=Monaco]Initializing built-in extension SYNC[/FONT]
[FONT=Monaco]Initializing built-in extension XKEYBOARD[/FONT]
[FONT=Monaco]Initializing built-in extension XC-MISC[/FONT]
[FONT=Monaco]Initializing built-in extension SECURITY[/FONT]
[FONT=Monaco]Initializing built-in extension XINERAMA[/FONT]
[FONT=Monaco]Initializing built-in extension XFIXES[/FONT]
[FONT=Monaco]Initializing built-in extension RENDER[/FONT]
[FONT=Monaco]Initializing built-in extension RANDR[/FONT]
[FONT=Monaco]Initializing built-in extension COMPOSITE[/FONT]
[FONT=Monaco]Initializing built-in extension DAMAGE[/FONT]
[FONT=Monaco]Initializing built-in extension MIT-SCREEN-SAVER[/FONT]
[FONT=Monaco]Initializing built-in extension DOUBLE-BUFFER[/FONT]
[FONT=Monaco]Initializing built-in extension RECORD[/FONT]
[FONT=Monaco]Initializing built-in extension DPMS[/FONT]
[FONT=Monaco]Initializing built-in extension Present[/FONT]
[FONT=Monaco]Initializing built-in extension DRI3[/FONT]
[FONT=Monaco]Initializing built-in extension X-Resource[/FONT]
[FONT=Monaco]Initializing built-in extension XVideo[/FONT]
[FONT=Monaco]Initializing built-in extension XVideo-MotionCompensation[/FONT]
[FONT=Monaco]Initializing built-in extension SELinux[/FONT]
[FONT=Monaco]Initializing built-in extension XFree86-VidModeExtension[/FONT]
[FONT=Monaco]Initializing built-in extension XFree86-DGA[/FONT]
[FONT=Monaco]Initializing built-in extension XFree86-DRI[/FONT]
[FONT=Monaco]Initializing built-in extension DRI2[/FONT]
[FONT=Monaco]Loading extension GLX[/FONT]
[FONT=Monaco]error setting MTRR (base = 0xf6000000, size = 0x00800000, type = 1) Invalid argument (22)[/FONT]
[FONT=Monaco]error setting MTRR (base = 0xf6000000, size = 0x00800000, type = 1) Invalid argument (22)[/FONT]
[FONT=Monaco]error setting MTRR (base = 0xf6000000, size = 0x00800000, type = 1) Invalid argument (22)[/FONT]
[FONT=Monaco]xinit: connection to X server lost[/FONT]
[FONT=Monaco]
[/FONT]
[FONT=Monaco]waiting for X server to shut down error setting MTRR (base = 0xf6000000, size = 0x00800000, type = 1) Invalid argument (22)[/FONT]
[FONT=Monaco](EE) Server terminated successfully (0). Closing log file.[/FONT]
[COLOR=#F5F5F5][FONT=Monaco]
[/FONT][/COLOR]


Can you anyone help me? Thanks!
PS: Sorry for my bad english.

---

### Post by mastablasta on 2015-10-08
servers usually do not use desktop GUI. if you want it I suggest using lightdm desktop mananger. still if you installed xubuntu desktop it should be there. maybe it is just not configured?!


[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

> **Help, I can't see my Desktop!**


Many things can go wrong in a graphics stack. If you can't see any graphics or see corrupt graphics the following might help: 
[LIST]
[*]You can get to a text terminal using alt-ctrl-F1.
[*]Check the LightDM logs in /var/log/lightdm.
[*]Stop LightDM with *sudo stop lightdm*.
[*]You can try LightDM again with *sudo start lightdm*.
[*]If you have another display manager you want to try (e.g. gdm) start that: *sudo start gdm*.
[*]You can set the default display manager by running *sudo dpkg-reconfigure lightdm*.
[*]Check your system is up to date, especially video drivers.
[*]File a bug. If you're not sure where the cause is (lightdm / unity-greeter / unity / X / kernel) file against lightdm and the bug will be triaged and reassigned.
[/LIST]


servers can be run using command line interface. but if you really want some GUI (I know I do) then I suggest looking for a web based GUI (you access and control server from another pc via web browser). such GUI's are for example Ajenti, Zentyal or Webmin (not supported but works well for many)...

---


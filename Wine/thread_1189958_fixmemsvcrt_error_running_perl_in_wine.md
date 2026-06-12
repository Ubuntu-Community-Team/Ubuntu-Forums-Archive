---
title: "fixme:msvcrt error running perl in wine"
date: 2009-06-17
forum: Wine
---

### Post by wbest on 2009-06-17
Hey, whenever I run the command (I have to call perl out of another directory to get it to run correctly, it finds the neccessary files easier):
 
[SIZE=2]C:\public\TradeSystem>C:\public\perl\bin\perl build70.pl -file=build.ts.ini[/SIZE]
 
[SIZE=2]I get the error:[/SIZE]
 
 
[SIZE=2]fixme:msvcrt:msvcrt_fdtoh wtf[/SIZE]
[SIZE=2]fixme:msvcrt:msvcrt_fdtoh wtf[/SIZE]
[SIZE=2]fixme:msvcrt:msvcrt_fdtoh wtf[/SIZE]
[SIZE=2]fixme:msvcrt:msvcrt_fdtoh wtf[/SIZE]
[SIZE=2]fixme:msvcrt:msvcrt_fdtoh wtf[/SIZE]
[SIZE=2]fixme:msvcrt:msvcrt_fdtoh wtf[/SIZE]
[SIZE=2]fixme:msvcrt:msvcrt_fdtoh wtf[/SIZE]
[SIZE=2]fixme:msvcrt:msvcrt_fdtoh wtf[/SIZE]
[SIZE=2]fixme:msvcrt:msvcrt_fdtoh wtf[/SIZE]
[SIZE=2]fixme:msvcrt:msvcrt_fdtoh wtf[/SIZE]
[SIZE=2]fixme:msvcrt:msvcrt_fdtoh wtf[/SIZE]
[SIZE=2]fixme:msvcrt:msvcrt_fdtoh wtf[/SIZE]
[SIZE=2]fixme:msvcrt:msvcrt_fdtoh wtf[/SIZE]
[SIZE=2]fixme:msvcrt:msvcrt_fdtoh wtf[/SIZE]
[SIZE=2]fixme:msvcrt:msvcrt_fdtoh wtf[/SIZE]
[SIZE=2]fixme:msvcrt:msvcrt_fdtoh wtf[/SIZE]
[SIZE=2]fixme:msvcrt:msvcrt_fdtoh wtf[/SIZE]
[SIZE=2]fixme:msvcrt:msvcrt_fdtoh wtf[/SIZE]
[SIZE=2]fixme:msvcrt:msvcrt_fdtoh wtf[/SIZE]
[SIZE=2]fixme:msvcrt:msvcrt_fdtoh wtf[/SIZE]
[SIZE=2]fixme:msvcrt:msvcrt_fdtoh wtf[/SIZE]
[SIZE=2]fixme:msvcrt:msvcrt_fdtoh wtf[/SIZE]
[SIZE=2]fixme:msvcrt:msvcrt_fdtoh wtf[/SIZE]
[SIZE=2]fixme:msvcrt:msvcrt_fdtoh wtf[/SIZE]
[SIZE=2]fixme:msvcrt:msvcrt_fdtoh wtf[/SIZE]
[SIZE=2]fixme:msvcrt:msvcrt_fdtoh wtf[/SIZE]
[SIZE=2]fixme:msvcrt:msvcrt_fdtoh wtf[/SIZE]
[SIZE=2]File not found[/SIZE]
[SIZE=2]Unable to set cursor, run 'cls' and then re-run this script. at build70.pl line 634.[/SIZE]
[SIZE=2]fixme:msvcrt:msvcrt_fdtoh wtf[/SIZE]
 
[SIZE=2]Now, this only happens with this program. I've tested "Hello, world!" and it ran successfully. So, I think this may just be a problem in the program itself, but its not very descriptive, so I have no idea where to start. Has anyone else seen this before?[/SIZE]
 
 
I'm running this in Hardy with win 0.9.59 (I have already fixed the "failed to reserve range" problem)

---

### Post by cogadh on 2009-06-17
Is there a reason you are using such an out of date version of Wine? You should try updating to a newer version, the "fixme" you are encountering may have already been addressed:
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by wbest on 2009-06-17
I just took it out of Add/Remove programs.
So whatever was in there (0.9.59), that's what I have.
 
Also, my boss wanted me to use Hardy, so I'm a little fearful newer version of Wine won't work as well in such an old distro.  Maybe living with Windows and Mac for too long has made me a little paranoid about OS versions becoming too old to run things...

---

### Post by cogadh on 2009-06-17
If you follow the link I gave you, it takes you to the official WineHQ package repository, which is built and maintained by the same person who maintains the Wine package in the Ubuntu repository. It is pretty much guaranteed to work perfectly with your version of Ubuntu. Besides, your version of Ubuntu is only a little over a year old now and is still actively supported, you don't really have to worry too much about "new software on an old OS" problems yet.

---


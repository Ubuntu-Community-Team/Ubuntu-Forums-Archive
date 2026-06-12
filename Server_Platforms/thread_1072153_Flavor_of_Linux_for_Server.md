---
title: "Flavor of Linux for Server"
date: 2009-02-17
forum: Server Platforms
---

### Post by Black Razor on 2009-02-17
Hey,

I have an old machine which only has a 400Mhz processor in it, and I think 256MB of RAM.  Bare bones, sorta.  HD Space not an issue.  I want to install some flavor that runs well and ultra fast with practically no computer requirements, GUI neccessary.  All it has to do is network to my Ubuntu box so I can use the old PC as a file server.

Couple of things would be nice:

#1 Debian based.  I am pretty invested in Debian/Ubuntu.  I don't really want to learn another flavor.
#2. It needs to be easy to use.  I'm a neophyte Linux user, but not a total newb.

So...what distro do you guys like an recommend?  Perhaps I should just use actual Debian for the server?  I mean maybe its time to start learning how to work from the shell more.  I am comfy launching/installing programs, and compiling (hate it btw, much prefer .debs)

I also kinda wonder, if I use Debian 5 with no desktop.  How do I admin from a GUI without a KVM Switch?  Also, does Ubuntu and Debian automatically work well together?  Would it be easy to network them?

---

### Post by Thirtysixway on 2009-02-17
I think damnsmalllinux is based off of debian?  It's lightweight but I've never really done much with it.

---

### Post by tarps87 on 2009-02-17
My suggestion if you are currently using Ubuntu would the the server edition, you can install a GUI onto it but I would suggest trying the command line, I think you will find it's not as difficult as you thing.
This guide will teach to how to set up a ssh connection so you can log into it from a remote machine and how to set up file share along with a lot of other useful information, you will probably only need to use a small section of it.
[https://help.ubuntu.com/8.10/serverguide/C/index.html](https://help.ubuntu.com/8.10/serverguide/C/index.html)

I am currently using the server edition of Ubuntu for a file, media and update server. It probably took about a day to set up including build and installing.
CPU: pentium 2 300MHz
RAM: 128MB

I can stream two video files and I file transfer before the video gets copy. (currently looking for a fan-less server :))

If you really need to use a GUI then xfce interface (Xubuntu) or fluxbox would be more suited to your needs

Hope this helps

---

### Post by mister_p_1998 on 2009-02-17
Freenas, I run it on a 1ghz Celeron with 256mb ram... perfect, serves 4 pc's as a fileserver.

---

### Post by songshu on 2009-02-17
eeuuuhhhh,

you are looking for a debian based server distribution???
what about eeuuuhhhh debian?

---

### Post by jimv on 2009-02-17
I agree with the guy who said go with the command line.  I have 4 Ubuntu servers running on old Dells with SSH, Apache, and SMB running, and they usually don't use much more than 100mb of RAM.

For a low resource "GUI", you could use Webmin, which is a web interface that will let you configure/monitor the server.

[http://www.webmin.com/](http://www.webmin.com/)

---

### Post by Iowan on 2009-02-17
I have servers running on P-200 and P-266 running Breezy and Hardy-LAMP.  They're not speed-demons, but I suspect they'd REALLY drag if I tried to run a GUI.

---

### Post by Black Razor on 2009-02-18
Good input.  Thanks!

---


---
title: "Need more info"
date: 2007-01-02
forum: Server Platforms
---

### Post by dude1701 on 2007-01-02
Hi


I am new to ubuntu. Oh heck, im new to Linux! But, i do need some more info before i make the switch. Is it possible to use the Ubuntu Server (6.10) as a web server so I can set up and host my own websites? Does it allways have to be running to allow people to access those websites? and, what are the system requirements. And one more thing, is there a way to use a program (such as Virtual PC for windows 2004) so I can run Ubuntu Server and Windows at the same time? Thanks for the help

---

### Post by mojoman on 2007-01-03
You can use Ubuntu server editions to host websites.

It has to be running for people to access the websites that it is hosting.

The system requirements for the server edition is a meagre 64 MB RAM and 500 MB HD (excluding HD-space for anything that you might actually want to host on the server). Read more on the requirements for the various editions here: [https://help.ubuntu.com/](https://help.ubuntu.com/)

I have no idea what Virtual PC is but you can't run two OS at the same time. However, there are emulators (such as Wine) that allows you to run windows-applications from Ubuntu so if Virtual PC is some sort of windows application I think chances are good that you'll be able to run it through Wine. That being said, I'll add that I've never used Wine so you might want to get a second opinon on this, especially if you want to use it with a server edition, which might not be possible as it lacks the x-server system, i.e. graphical support.

Hope this helps.
/Mojoman

---

### Post by Iowan on 2007-01-03
I haven't done it, but yes, Ubuntu can be set up as a web server (LAMP = Linux, Apache, MySQL, PHP).  Here's one way:
[http://howtoforge.com/ubuntu_debian_lamp_server]("http://howtoforge.com/ubuntu_debian_lamp_server")
I would imagine that it would need to be running to serve up web pages...:confused: 
System requirements vary - depending on whether you install the desktop. I have a file server running on lower end machine (p2-200Mhz/128MB), but that's on a 10BaseT home network. 
WINE is a program that can be used to run (some/most, but not all) Windows programs on a Linux machine, but I don't know if (or how well) it runs concurrently.
BTW, for a server, you may want to consider 6.06 LTS (long term support).

---

### Post by zekopeko on 2007-01-03
> **mojoman said:**
> 

I have no idea what Virtual PC is but you can't run two OS at the same time.


/Mojoman

wrong. you can use vmware ([http://www.vmware.com)](http://www.vmware.com)). the server version is free and pretty fast.

on my computer (look in the sig) it runs without any problem and at native speed.

---

### Post by mojoman on 2007-01-03
> **zekopeko said:**
> wrong. you can use vmware ([http://www.vmware.com)](http://www.vmware.com)). the server version is free and pretty fast.

on my computer (look in the sig) it runs without any problem and at native speed.

Cool. Roughly, it's the same principle as running something in a chroot environment, right? Anyway, I didn't know about this but what I meant was that you cannot boot into two OS at the same time.

/Mojoman

---


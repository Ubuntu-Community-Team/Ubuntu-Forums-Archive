---
title: "how to do an image backup of a hosted ubuntu server 10.04.3 LTS ??"
date: 2012-03-02
forum: Server Platforms
---

### Post by kdaffef on 2012-03-02
Hi the best forum,
As i'm new in this forum and in Linux world, i have small and easy question for you.
I have a hosted ubuntu server 10.04.3 LTS, i can access to it with ssh and ftp.

Nowadays I need to backup the whole of its disk to an image that i can save it at my office to install it if problem ....

I used to use clonezilla live cd on an asterisk local server and its extremely fast ...

Could do the same method (how?) with the hosted server ?

Any idea or tuto for a beginner ???

Big thank

Kamel

---

### Post by aeiah on 2012-03-02
this is only possible if the hosting company offers some kind of service, really. if you image the whole drive, the operating system can't be running. if the OS isn't running, you can't get access to do the imaging :p

you could try rsync. i have heard that you can backup an entire operating system with it whilst the system is running, but it isn't just a case of rsyncing the whole thing - there are various areas that need to be excluded (like /proc and /dev )

---

### Post by kdaffef on 2012-03-03
> **aeiah said:**
> this is only possible if the hosting company offers some kind of service, really. if you image the whole drive, the operating system can't be running. if the OS isn't running, you can't get access to do the imaging :p

you could try rsync. i have heard that you can backup an entire operating system with it whilst the system is running, but it isn't just a case of rsyncing the whole thing - there are various areas that need to be excluded (like /proc and /dev )


yes, you re right ;)
I will check my IS provider to see if they propose an offline backup solution ??

thanks

---


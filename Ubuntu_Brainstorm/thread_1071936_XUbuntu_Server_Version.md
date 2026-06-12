---
title: "XUbuntu Server Version"
date: 2009-02-16
forum: Ubuntu Brainstorm
---

### Post by 1222tmiller on 2009-02-16
Hi, 

I am a Windows guy desperately wanting to move to Linux.  Unfortunately, well done server utilities / wizards are far and few. In addition, if I am not administering the server, it would be nice to turn off the UI.  XUbuntu seems like the perfect candidate to be a Server UI.  Unfortunately I have already wasted days trying to find a "How To" on installing XUbuntu user interface on the server version. I am still wasting days of research on finding the right utilities and wizards for admining normal server functionality, full management of hard disks.

It would also be nice when the server comes up to have it default to text mode, but have an easy way to choose a graphical interface.  In addition, a wizard for remoting in to manage the server graphically.  Yes this can be done, because I see people explaining how to do it, unfortunately I have yet to get any of the "How To"s to work. :-( 

For a small business or home system, Hard Drive, Users, Remoting, and Samba graphical controls.  Please note, when I say hard drives, let's say I add a new hard drive into the computer, I want to be able to select it, partition it, and select auto mount each partition.

---

### Post by Gen2ly on 2009-02-16
Linux is well known for it's ability to be a server.  In fact most kernel developments are about adding server abilities.  Yes, I know what you're thinking that a server gui would be very very nice.  Server tend to run mean and lean to be able to handle a good amount of resource they are alot of times required to do.  There are various tools like firestarter for a firewall (though I don't recommend it) and [mounting utilites]("http://www.linux.com/feature/153412").  There's probably a linux distro like what you are looking for.  Try to google "Linux server gui" or something like that.

Good luck.

---

### Post by cdenley on 2009-02-17
I think I've heard Mandriva has nice GUI wizards. I've never tried it before.

> 
Unfortunately I have already wasted days trying to find a "How To" on installing XUbuntu user interface on the server version.


It's very simple, and I'm sure it has been mentioned on this forum before.
```

sudo apt-get install xubuntu-desktop

```

---

### Post by 1222tmiller on 2009-02-17
I tried that and it didn't work.  Missing several x-server components and configuration stuff.  That would be a solution, to include the xubuntu desktop as an install option on the server addition. I just wish Linux folk weren't so negative about GUI management tools.  Heck, our brand new AIX stack at work is all web GUI managment tools now.  You only go to the command line if you absolutely have too.

---

### Post by cdenley on 2009-02-17
> **1222tmiller said:**
> I tried that and it didn't work.  Missing several x-server components and configuration stuff.  That would be a solution, to include the xubuntu desktop as an install option on the server addition. I just wish Linux folk weren't so negative about GUI management tools.  Heck, our brand new AIX stack at work is all web GUI managment tools now.  You only go to the command line if you absolutely have too.

You probably don't have all the repo's enabled that you need, don't have an internet connection, or haven't done a "sudo apt-get update" recently.

I just wish Windows folk weren't so negative about CLI tools and configuration files. All the server components and xubuntu components probably wouldn't fit on the CD. Also, probably most people who download the server CD, myself included, would not want to waste bandwidth downloading xubuntu components.

I don't think GUI tools will ever be an acceptable substitute for editing configuration files. It might help new users who aren't familiar with how to configure linux servers, but probably most server admins would prefer  a terminal. There is only so much tools like webmin or firestarter can do.

---

### Post by Gen2ly on 2009-02-17
> **1222tmiller said:**
> ...I just wish Linux folk weren't so negative about GUI management tools.  Heck, our brand new AIX stack at work is all web GUI managment tools now.  You only go to the command line if you absolutely have too.

That's thinking ideally.  Developers are busy adding what's needed.  If someone likes to come about later and add a gui frontend that's great.

---


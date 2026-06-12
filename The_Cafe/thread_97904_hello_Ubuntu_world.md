---
title: "hello Ubuntu world"
date: 2005-12-01
forum: The Cafe
---

### Post by lleb on 2005-12-01
Hello all, I just joined this forum, and hope it is as friendly and as kind as the LinuxQuestions.org forum I frequent.

I am here more for the new edubuntu then ubuntu on its own, but that does not mean I am not going to check out kubuntu (i like kde better then gnome) as ai have been an avid Debian fan for about 18 months now.

I started messing around, for real this time, with Linux just before RH9 was dropped from support and FC1 was just in the book stores.

I started with RH9 and now run both CentOS 4.2 and Debian testing.  I still like the Debian over the RH line of distros, but my web/e-mail server is running on a RHE fork called Whitebox.  Soon to be upgraded to a CentOS system I hope.

Looking forward to some good community banter and learning about kubuntu and edubuntu.

:p :p :p

---

### Post by atoponce on 2005-12-01
[quote=lleb]Hello all, I just joined this forum, and hope it is as friendly and as kind as the LinuxQuestions.org forum I frequent.[/quote]

Oh, we are by far more friendly than LinuxQuestions.  :)

Seriously, welcome.  You'll enjoy it here.  BTW- how do you enjoy using CentOS?  I have heard a little about it, and wanted to put it on a test box I have at home.  I have been a little skeptic, however, between CentOS 2, 3 and 4.  What are the differences?  Are they based off of software package bundles?  Also, isn't CentOS an RPM based distro?  I don't know if I can learn a new package management system, as apt-get is the best ever!

---

### Post by KiwiNZ on 2005-12-01
Welcome aboard

---

### Post by SweetDreams on 2005-12-01
Hi, welcome to the forum.

---

### Post by ubuntu27 on 2005-12-02
Hi, welcome to the Ubuntu community lleb.
Yes, this forums is really friendly :) too friendly that it makes you wonder if they know you in real life :P

---

### Post by Pablo_Escobar on 2005-12-02
RTFM !!!!

Ooops this isn't a Slackware forum :D

Welcome mate and feel free to ask any questions, I bet someone will be knowledgable enough to help You :)

---

### Post by lleb on 2005-12-02
[QUOTE=atoponce]Oh, we are by far more friendly than LinuxQuestions.  :)

Seriously, welcome.  You'll enjoy it here.  BTW- how do you enjoy using CentOS?  I have heard a little about it, and wanted to put it on a test box I have at home.  I have been a little skeptic, however, between CentOS 2, 3 and 4.  What are the differences?  Are they based off of software package bundles?  Also, isn't CentOS an RPM based distro?  I don't know if I can learn a new package management system, as apt-get is the best ever![/QUOTE]


CentOS is a fork of RHE so the 2, 3, and 4 are from RHE2 RHE3 and RHE4 the most current being 4.2.

Yes it is a rpm based distro.  I have to say it handles being a NFS client way better then debian does.  Only reason I put it on my laptop was for the fact that I still do not know enough to build and manage 100% my own server.  I have a guy in my LUG setup and configure a server for me.  He is most comfortable with the RH line of distros so he choses CentOS as his flavor.

Currently I have my web and e-mail hosted on his WhiteBox server (this is a fork from RHE3), but may be moving it back to my office and when I do, it will be on CentOS 4.x.

As for how I like it as a server, i love the RHE forks.  they give me plenty of stability, they make updating the kernel easier then any other distro i have used, and when you update things, they just work.  In a server enviroment that is more important then just about anything.  downtime = evil *grins*, thats why MS servers suck so much compaired to linux.  their downtime is 2 - 4x as much as my linux servers.

[edit to add]

YUM is the package manager for CentOS as it is for all RH line of distros.  Yum is much slower, but just as affective as apt for handling dependancies and what not.  Its big problem is the time it takes to read all of the headers, verify them, etc...  

My debian respositories are rather large and customized for personal use, but my CentOS repository is only a few lines and it takes 3 - 4x as long to yum update as it does to apt-get update.  that is when cron is your friend.  you can have cron run  your yum update automatically for you, then later you can come back and yum -C update and cut the time for yum to do its thing in half.  still slower then apt, but eh no biggy at that point.

---


---
title: "New to Ubuntu Server"
date: 2012-05-20
forum: Server Platforms
---

### Post by richardc007 on 2012-05-20
Hi All

I to am a newby and about to setup a server. open to suggestions on equipment minumin and is there a setup page to do the full install. also the setup for lampp to be added if needed

Many thanks
Richard:lolflag:

---

### Post by lisati on 2012-05-20
*Post moved to own thread in **Server Platforms**.*

System requirements can depend on what you have in mind for your server.

Some information can be found at [https://help.ubuntu.com/12.04/serverguide/index.html](https://help.ubuntu.com/12.04/serverguide/index.html)

---

### Post by 2F4U on 2012-05-20
Ubuntu Server, by default, comes without GUI and you can choose the services that you want. That makes it very flexible. I once installed it on an old Pentium4 with 4GB RAM and used it as file server. You can also do some setup testing in a virtual machine, just to get a feeling for how it is.

---

### Post by LHammonds on 2012-05-20
> **richardc007 said:**
> I to am a newby and about to setup a server. open to suggestions on equipment minumin and is there a setup page to do the full install. also the setup for lampp to be added if needed

Then I would strongly suggest installing VirtualBox on your PC and get familiar with installing and running an Ubuntu server.   There are many times when you are first learning the system that you will want to start over or wipe out a change you just made.  If you do this in a virtual machine, you can take snapshots along the way and if you need to backup, simply revert to your last snapshot and avoid having to start all over from scratch.  This will save you a LOT of time until you get familiar with the process and it will allow you to know almost the exact steps you need to take when installing on your physical server.

Installation can be as simple or complex as you need it.  Inserting the CD, booting up and answering a few basic question (such as selecting SSH and LAMP options) can get you running very quickly.  However, you might want to learn a bit about the underlying partition system upon which your server will run.   For example, if your "root" partition gets full and runs out of space, it will cause all kinds of headaches for you.  It is best if you can separate the root partition from your other fast-growing partitions so if your database or web site fills up the storage, it will only fill up its own storage and not the entire system.  You will also want to learn how to "grow" your storage when adding new drives.

All of this can be safely learned inside a virtual machine.  :)

Here are [_my notes for setting up a MediaWiki server_]("http://ubuntuforums.org/showthread.php?t=1979266") which details my data needs and growth concerns and then shows how to implement the plan with a step-by-step installation of Ubuntu server.

LHammonds

---


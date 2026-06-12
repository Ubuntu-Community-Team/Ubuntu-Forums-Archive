---
title: "Dell R710 supported?"
date: 2009-05-18
forum: Server Platforms
---

### Post by radiognome on 2009-05-18
Dear forum-readers,

Does anyone have (good) experiences with running Ubuntu on a Dell R710 server with a Perc6/i raidcontroller and a broadcom 5709 eternetcard?

I have searched the web, and this forum somewhat, but have not found any clues.

Kind regards,

Martin

---

### Post by erikthered81 on 2009-06-15
I'm looking for some info on this too.  I successfully installed i386 Hardy on an R610, but I needed to install x86_64.  When I boot the x86_64 installer, I select the language, hit enter, and immediately I get an error:

Kernel alive
Cannot find a valid memory mapPANIC: early exception rip ffffffff8021ff50 error 0 cr2 ffffffffff5fb030



Any clues!?  Thanks!

---

### Post by radiognome on 2009-06-15
I happen to have installed Jaunty on the R710 without any problems. The machine is purring like a kitten.

I was worried about the new Broadcom Ethernet-card, but it was detected flawlessly by the installer. (I ordered an older intell-card with it, to be sure, so I was asked which one of the 8 nic's I wanted to use during install).

Perhaps you should try 9.04. It is no LTS, but it at least lasts most of the functional lifetimes of the server-configurations I build.

---

### Post by netangel on 2009-07-06
You can find the answer here : [https://bugs.launchpad.net/ubuntu/+bug/386086](https://bugs.launchpad.net/ubuntu/+bug/386086)

---

### Post by plamen_f on 2010-09-15
For NIC & RAID - don't worry - the works fine with 8.04 & 10.04.

But I have other problem.

I test R71o with 2x5620, 12GB of RAM & 2x300 15k SAS. Using Ubuntu 8.04 and firebird2.0.5 as Database for enterprice app I see huge performance. This machine was 30% slower than another one - Intel 1x3430 8GB, 2x500 SATA - soft RAID.

Googling a couple of days I realise that the problem is in rescheduled interrupts. Dell generate millions/hour while Intel 10 or 20...

When I try to ask DELL support for any idea - just recieved: this is not enterprise OS, we do not supoort any solutions like this!

---


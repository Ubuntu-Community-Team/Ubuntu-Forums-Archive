---
title: "[SOLVED] 8.04.1 install works on some servers, but not all"
date: 2008-09-16
forum: Server Platforms
---

### Post by nathan42100 on 2008-09-16
As some of you already know, I'm doing a project for school. During my installation, I installed 8.04.1 successfully on 3/5 Dell PowerEdge Servers. They were all 2400s. I tried to do it with the same disks on the other two (2500s) and they both failed. On both computers, I rand a disk check and they both failed with a packages.gz corruption. 6.04 works just fine. Any idea why?

:confused::confused::confused:

---

### Post by nathan42100 on 2008-09-17
no ideas?

---

### Post by kaltsi on 2008-09-17
Do you use raid option?

---

### Post by nathan42100 on 2008-09-19
I don't think so...

---

### Post by ascii2k8 on 2008-09-19
I wish I had something to tell you to help.   All I know is this sounds a whole lot like the problem I had.  I was only trying to install on one server but it wont work no matter what I try.  But it works perfect on my laptop.  Lotta good that does me. lol

---

### Post by pjbgravely on 2008-09-19
I believe I am having the same problem with an HP netserver E 800. The install dies while installing defconf preconfiguration file. It dies at 0%,3%, or 33%. I tried changing the CD-ROM and adding boot parameters with no change. I am going to try installing off a hard drive like I had to do when the kernel couldn't even see the CD-ROM but I don't see an easy way to do that like with SUSE. I will let you know when I have solved this problem.

Paul

---

### Post by nathan42100 on 2008-09-19
I fixed it. It had something to do with the CD-ROM drive being SCSI. So I got an IDE controller and hooked up an IDE drive and it installed fine.

---

### Post by cariboo on 2008-09-20
Did you create a bug in:

[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

This will help other people with the same problem.

Jim

---


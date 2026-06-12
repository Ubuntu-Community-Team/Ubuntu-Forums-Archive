---
title: "About release development"
date: 2009-02-07
forum: The Cafe
---

### Post by codedash on 2009-02-07
Hi everyone. I need some help to undestand this.
I know that ubuntu is based on debian and every six months there is a release.
In the beginning ubuntu repos start fill from debian until the freeze time, then through a proccess we have a release.
What i dont understand:
The developers work on the last ubuntu to create the new one (updating/adding features/fixing bugs etc) or they have some pieces of code that make ubuntu user friendly eg easy installer, add/romove etc and built each release from scratch based on a clean debian?
I have a feeling that the second happens and makes me think that the outcame can not mature through time because the release is made from scratch each time, although it has the latest software.
Any answer is very much appreciated.

---

### Post by igknighted on 2009-02-07
This will probably get moved to the cafe, it's not really a support request...

I think the two options you list are not mutually exclusive.  There are some Ubuntu devs that are working on Ubuntu specific apps (such as the Ubiquity installer and the Hardware Drivers app), but most Ubuntu development is done by people completely unrelated to Ubuntu.  Ubuntu just packages up their work and distributes it.  Aside from a small handful of apps, the jobs of the Ubuntu developers is to make applications work nicely together.  This process has to be done each time, as new versions of apps require different tweaks to play nice together.

In this sense, Ubuntu is a little different than other distros.  Red Hat/Fedora and Novell/Opensuse both play major roles in upstream development like the kernel, gnome, KDE and other projects, but they have major corporate backing and far more developers, so there is more manpower to work on other stuff.

---

### Post by codedash on 2009-02-08
Thanks for answering. You cleared this a lot. So if i get it correct, there is a pool with packages/prgrams that are maintaned and each distro picks their according to their philosophy, organizes, tests and makes a release. Ubuntu has desktop in mind so makes some programs that make things easier, suse makes yast etc?
So why ubuntu had to be based on debian and not make just ubuntu? I have read the advantages, but why they couldnt make a standalone distro like suse, fedora?

---

### Post by bomanizer on 2009-02-08
> **codedash said:**
> ...
So why ubuntu had to be based on debian and not make just ubuntu? I have read the advantages, but why they couldnt make a standalone distro like suse, fedora?

Superior package management? I dunno, but I always had the feeling that Ubuntu is all about package management, and in my experience, no one does this better than Debian.

---

### Post by cariboo on 2009-02-08
If you start looking at different distributions you will find that most of them are based on either rpm or deb packages. RPM stands for **R**ed Hat **P**ackage **M**anager and DEB is short for Debian.

It is much easier and quicker to create a distribution form the package reposiotires then it is to come up with a whole new packaging scheme and then create the packages from source.

Jim

---

### Post by igknighted on 2009-02-08
> **codedash said:**
> Thanks for answering. You cleared this a lot. So if i get it correct, there is a pool with packages/prgrams that are maintaned and each distro picks their according to their philosophy, organizes, tests and makes a release. Ubuntu has desktop in mind so makes some programs that make things easier, suse makes yast etc?
So why ubuntu had to be based on debian and not make just ubuntu? I have read the advantages, but why they couldnt make a standalone distro like suse, fedora?

It takes a lot of work to build everything from scratch.  You need a lot of developers to build everything from scratch.  Essentially, by basing off of Debian, a lot of the work is done, and it's just the finishing touches that are left to put on the release.  Since Ubuntu is a pretty small project relative to other major distros, having to build the whole thing would not let them do the little things that make Ubuntu different.

---

### Post by codedash on 2009-02-11
Thanks for the answers. To make it completly clear for me:
When i think that ubuntu is debian based, i get the picture of taking debian, then cuting/copying/paste code and making ubuntu. So after this makes me feel that from something "stable" i will get a remix with flaws (off course i dont say that debian is flawless but you know,the outcome/ubuntu is more) because the main debian was edited. So i m thinking getting debian just to have the original release although ubuntu's lifestyle suits my needs.
Help me get this right and ease my self with Ubuntu.
(I hope i m not saying tooo stupid things)

---


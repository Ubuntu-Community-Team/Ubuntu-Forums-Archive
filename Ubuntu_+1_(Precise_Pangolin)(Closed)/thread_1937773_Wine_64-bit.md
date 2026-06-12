---
title: "Wine 64-bit"
date: 2012-03-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by svtguy88 on 2012-03-08
Hey all, my 12.04 install gets more and more stable every day I update it, and most of my annoying problems have disappeared.

I'm trying to install Wine, as I want to try and get SAPGui working under it (school gives me a Windows installer and an OS X program...nothing for linux).  Anyway, I went to Synaptic, and noticed that Wine wants to install a LOT of 32 bit dependencies...making me think I'd be stuck with a 32 bit version of Wine.  Not a huge deal, but why?

I went to the Wine pages, and couldn't really find much.  This [page]("http://wiki.winehq.org/WineOn64bit#head-245e8f90708da8070a4f3cbe336254c712af07e2"), and specifically the "Ubuntu Way" section, points out that 12.04 has multiarch support, which could cause problems when building 64 bit Wine from source.

Anyone have any luck?  I'm sure I could just get by with 32 bit Wine, but I'd rather know why this doesn't work, and why the Wine pages say that building 64 bit under 12.04 may ruin "your ability to build 64 bit programs."

Maybe I'm reading the pages wrong.  Can someone clarify?

---

### Post by Gavin77 on 2012-03-08
It installs those files because it doesn't use ia32-libs anymore.

---

### Post by grahammechanical on 2012-03-08
Why do you not install through the software centre. Because we are 12.04 we get wine 1.4. Which I think is the most up to date version. it is 1.4~rc6-0ubuntu.

I originally (months ago) I installed wine through this ppa

> [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) precise

But I do not use it now as I am getting updates through Update Manager.

Ubuntu is switching over to something called multiarch. I think that it means having libraries that make 32bit applications work better on a 64bit Ubuntu without installing special 32bit libraries. May be the multiarch libraries that are being developed work with either the 32bit version of the application or the 64bit version of the application. One set of libraries serving both the 32bit and the 64bit versions of applications. I am not sure of this.

I also think that may be wine does not have a pure 64bit version. Anyway, I would suggest installing the version in the software centre.

Do you have any intention of building 64bit programs? 

Regards.

---

### Post by svtguy88 on 2012-03-09
I do some development work on this machine, nothing too major, but the idea of "losing capabilities" seems wrong.

Anyway, I'll just install from Synaptic most likely.  I only need Wine for some really basic stuff, as I have a VirtualBox install and a dual boot.  I was just a bit confused as to the wording.

I didn't like all of the 32-bit dependencies that Synaptic wanted to install, so I thought I'd compile and install from source to avoid unnecessary packages.

---

### Post by fantab on 2012-03-10
Install PLAYONLINUX from Ubuntu Software Center... it also installs Wine 1.4 and all the required dependencies and libraries. Also, I find installing Wine via Playonlinux much more stable and reliable than just Wine on its own. And I don't know why.

---

### Post by dino99 on 2012-03-10
Strangely rc5 was having a wine1.4-amd64 package, but the rc6 into precise archive have not

[https://launchpad.net/~scottritchie/+archive/build-tests/+packages](https://launchpad.net/~scottritchie/+archive/build-tests/+packages)

maybe Scott have forgotten to publish one; time to report that issue.

note: the rc6 for amd64 can be found here: [https://launchpad.net/~ubuntu-backports-testers/+archive/ppa/+packages](https://launchpad.net/~ubuntu-backports-testers/+archive/ppa/+packages)

---


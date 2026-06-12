---
title: "Ubuntu Clustering (mosix)?"
date: 2006-10-28
forum: Server Platforms
---

### Post by funkyade on 2006-10-28
Just wondering (again) if anyone has managed to get an Ubuntu cluster going using the latest development versions of OpenMOSIX?

Not getting very far myself at the moment, have got a small number (5) of old machines going using ClusterKnoppix quite easily, however, it uses the 2.4 kernel and is i386 only. I have a variety of hardware available that I want to cluster, x86, ppc, sparc, and compiling individual kernels is a nightmare - it doesn't work as yet. I'm using the info at [http://tab.snarc.org](http://tab.snarc.org) as a start point, what got me started on this were the attached documents, all of these are based on the 2.4 kernel.

If I had more time, energy, and expertise to pursue this I reckon it could be workable. Anyone got any other views?

UPDATE: Just came across this guide [http://www.gentoo.org/doc/en/openmosix-howto.xml](http://www.gentoo.org/doc/en/openmosix-howto.xml) they even have patched sources you can 'emerge', although still 2.4 kernel. Had to be Gentoo...

---

### Post by Chayak on 2006-10-29
[openmosix]("http://www.openmosix.org") is a fairly easy setup though as mentioned they currently only support the 2.4 kernel.  There is 2.6 support in the works.  Check their site in the link it should give you some better docs

---

### Post by funkyade on 2006-10-29
UPDATE: using gentoo and the openmosix-sources 2.6.12.577 I have managed to get an old x86 (P2-266) laptop up and running and an old iBook (G3-500). Stuff appears to work okay, with no extra configuration needed except that which is given in the [Gentoo OpenMosix WIKI page]("http://www.gentoo.org/doc/en/openmosix-howto.xml"). I'm getting about 1200 bogomips with these two machines... 400 for the x86 and 800 for the G3. I think the G3 is underachieving here for some reason...(?) :confused: 

Next job is to try and work out how to port this to Ubuntu... Anybody ported a gentoo kernel to Ubuntu? :-k 

...And then after that it's to try and use PXE so I can have diskless nodes... :-#

---

### Post by funkyade on 2006-11-25
UPDATE:

Have compiled a vanilla kernel with openmosix patch for 2.6 (it's 2.6.17) on Ubuntu. It didn't require much tweaking and runs mostly okay (it's a bit faster too). I have had a few random crashes in stuff I didn't have crashes in before so am currently trying to work out why. However, this does look promising. This link helped greatly - [http://www.ubuntuforums.org/showthread.php?t=217657](http://www.ubuntuforums.org/showthread.php?t=217657)

I will attempt to post a .deb once I get this stable, although I haven't got a clue where to start, apart from using checkinstall.

---

### Post by yuni on 2006-12-14
> **funkyade said:**
> UPDATE: using gentoo and the openmosix-sources 2.6.12.577 I have managed to get an old x86 (P2-266) laptop up and running and an old iBook (G3-500). Stuff appears to work okay, with no extra configuration needed except that which is given in the [Gentoo OpenMosix WIKI page]("http://www.gentoo.org/doc/en/openmosix-howto.xml"). I'm getting about 1200 bogomips with these two machines... 400 for the x86 and 800 for the G3. I think the G3 is underachieving here for some reason...(?) :confused: 

Next job is to try and work out how to port this to Ubuntu... Anybody ported a gentoo kernel to Ubuntu? :-k 

...And then after that it's to try and use PXE so I can have diskless nodes... :-#

How wonderful it is. Does it work fine? I have been wroking in gentoo with  [URL="http://www.gentoo.org/doc/en/openmosix-howto.xml"] but I can not have any luck.

How can you do that? Could you possibly write some mini-howto's?  I use openmosix with cluterkoppix. It is easy to install but very hard to update other packages. I tried it in Ubuntu but after kernel compilation when I reboot my desktop, the kernel is panic.

I started gentoo last week because the Wiki is so promossing but I can not get it. I used openmosix-2.4.x sources using ```
 emerge openmosix 
``` 

Thank you in advance.

---

### Post by funkyade on 2007-01-08
Hi

Not been here much lately as I've shifted all but one of my machines over to Gentoo/Kororaa.

I couldn't improve the stability of the Ubuntu OpenMosix setup that I had and ended up abandoning the idea for the foreseeable future in favour of a setup (Gentoo) that works.

I originally used the same setup as you have tried, a ClusterKnoppix head-node, but I used CHAOS1.6 for the nodes as you just boot from the CD and you have an instant node without any overhead. The main drawback with this setup is that it is 2.4 kernel based. I really need to have 2.6 as I can get architectures other than x86 working with it, 2.4 is x86 only as far as I am aware...

I'm not going to post any Gentoo how-tos here as that would be taking the mickey, as it is an ubuntu forum, however, you only really need to emerge all the appropriate packages and do a small amount of setting up - I compiled one kernel on my fastest machine and copied that to my nodes. It then just works, mostly - some applications don't migrate very well, particularly Java ones.

Hope this was of help in some way?

---

### Post by ajt on 2007-01-11
I've just posted this on the openmosix-general mailing list:

[https://lists.sourceforge.net/lists/listinfo/openmosix-general](https://lists.sourceforge.net/lists/listinfo/openmosix-general)

Hello, openmosix-general.

I've successfully upgraded our 'old' 64-node openMosix Beowulf cluster to Ubuntu 6.06.1 LTS running a linux-2.4.26-om1 kernel compiled from the openMosix 2.4 CVS sources patched to be compatible with binutils 2.16:

[http://www.kernel.org/pub/linux/devel/binutils/linux-2.4-seg-4.patch](http://www.kernel.org/pub/linux/devel/binutils/linux-2.4-seg-4.patch)

I compiled linux-2.4.26-om1 using gcc-3.3, by setting the $(HOSTCC) and $(CC) variables in the Makefile to gcc-3.3. I've taken the opportunity to replace files checked out from the CVS that only differ from the kernel.org files in their SCCS/RCS headers, and #ifdef'ed a few of the openMosix 2.4.26-om1 changes to the kernel.org sources that are not marked as such in the openMosix 2.4.26-om1 CVS sources.

I've run the openMosix stress test several times now, and I think the kernel is quite stable. However, I'd be interested to hear from other people who use or want to use openMosix under Ubuntu or Debian Etch: The problems are essentially the same in both Ubuntu and Etch. Please post your replies here. I'll summarise this on the openMosix wiki when I know who else is working on openMosix linux-2.4.xx-om1 under Ubuntu/Etch.

I have not yet debugged my version of linux-2.4.34-om1, which has a bug in set_brk() when I try to use "mosrun". I now have to get on with other work, but I'll continue trying to get linux-2.4.34-om1 running, so I can use SATA drives with the "sata_nv" module on our new Tyan-based servers.

Best wishes,

    Tony.
-- 
Dr. A.J.Travis,                     |  mailto:ajt@rri.sari.ac.uk
Rowett Research Institute,          |    [http://www.rri.sari.ac.uk/~ajt](http://www.rri.sari.ac.uk/~ajt)
Greenburn Road, Bucksburn,          |   phone:+44 (0)1224 712751
Aberdeen AB21 9SB, Scotland, UK.    |     fax:+44 (0)1224 716687

This is a follow-up to my previous message there:

Hello, openmosix-general.

I've been running a linux-2.4.26-openmosix1 kernel with Red Hat 9.0, and Debian Sarge on our Beowulf cluster here for several years and it's been quite reliable. However, when the FedoraLegacy project announced the end of support for Red Hat 9.0 I started to think about an upgrade strategy.

My first step was to install Debian Sarge on one of the servers, which I did two years ago(!) and run the same linux-2.4.26-openmosix1 kernel. Since then, I've tested most of the software we use under Debian Sarge, and it all works fine. However, I quickly discovered that I couldn't recompile the openMosix kernel anymore when I upgraded to Debian Etch...

I now know the reasons why: I've applied the 2.4 kernel patches from the binutils-16 release, and modified the top-level Makefile to use gcc-3.3. During the course of this work, I looked at Ubuntu and, in particular, Ubuntu 6.06.1 LTS as an alternative to Debian Etch. I'm using Ubuntu for another project and, I've found it to be quite a nice system to use.

I realise that the all openMosix developers are working hard on the 2.6 openMosix kernel, but I wonder if anyone is still interested in the 2.4 openMosix kernel?

To cut a long story short, I patched the vanilla 2.4.34 kernel sources from kernel.org using the openMosix-2.4.26-1.patch then corrected the failures manually and edited the binutils-16 changes into openMosix. I then compiled a linux-2.4.34-om1 kernel under Ubuntu 6.06.1 LTS.

I've now got a two-node linux-2.4.34-om1 cluster running under Ubuntu 6.06.1 LTS, which required some minor fiddling with /dev/MAKEDEV and /etc/modprobe.conf. Automatic process migration is working, but mosrun fails because of a problem with set_brk(). I'm debugging that now, but I'd appreciate help from anyone else who's interested in an updated 2.4 kernel while the 2.6 kernel is being tested. I chose the 2.4.34 kernel because this is currently the 'stable' 2.4 kernel on kernel.org.

I'll create a 'deb' package of the kernel when I've got it working :-)

Happy New year!

    Tony.
-- 
Dr. A.J.Travis,                     |  mailto:ajt@rri.sari.ac.uk
Rowett Research Institute,          |    [http://www.rri.sari.ac.uk/~ajt](http://www.rri.sari.ac.uk/~ajt)
Greenburn Road, Bucksburn,          |   phone:+44 (0)1224 712751
Aberdeen AB21 9SB, Scotland, UK.    |     fax:+44 (0)1224 716687

---


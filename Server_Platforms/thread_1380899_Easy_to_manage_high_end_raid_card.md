---
title: "Easy to manage high end raid card?"
date: 2010-01-14
forum: Server Platforms
---

### Post by spookware on 2010-01-14
Hello all.

I am in need or a high end RAID card for Linux and want to see what everyones opinions are on which is best with respect to manageability. The card needs to be high end in that it should support a rather large battery backed RAM cache.

Why am I asking? Well I have had good luck with the recent LSI megaraid chipsets in terms of the kernel driver and performance. In fact they are great. Only problem is the LSI management application is simply horrible. Any of the open source alternatives don't support the newer chipsets like the one in my Dell T710 server.

So I figured I would ask around and see what others like. I am currently leaning towards an Areca ARC-1680ix-12 because of the large 4GB write back cache and the fact that you can manage it with its own built in ethernet connection (i.e. no crappy host based management apps ala LSI).

Anyone have any manageability related experience with either the areca cards or the adaptec ones?

Thanks in advance,
spookware

---

### Post by tgalati4 on 2010-01-22
I'm familiar with the built-in LSI megaraid (PERC 4/DI) in my dell poweredge 1750.  What specific management functions are you trying to perform?

I'm running Dell's OpenManage Server Administrator (omsa) and you can observe and take disks offline through a secure webpage.  There are command line tools as well.  It was developed for Red Hat, but has been ported to Debian.  Depending on your hardware, you might be able to install it and omsa will recognize the LSI card and gather statistics and be able to control it.

The PERC 4/DI card has a lithium battery and 128 MB of battery-cache.

Also the poweredge LSI megaraid has a substantial BIOS-based configuration utility for adding/removing, mirroring, hotswapping disks.

---

### Post by spookware on 2010-01-26
Well, unfortunately the ported OMSA deb files that are available are to old to work with the recent LSI chipsets. 

On my dell T710 I have to use the LSI command line program that is closed source and undocumented. Some nice folks have done the job of writing up some documentation on it but it is just not a good program. I have to poll it in a daemon or a cron job. It is serviceable but that is as much as I can say about it. Having said that it is preferable to trying to port a more recent version of OMSA to debian on my own.

You are correct about the very nice EFI based configuration utility. Problem is, half the reason to have RAID is so that I don't have to take the server offline to replace a bad disk. So the EFI based configuration tools don't help much except for initial setup.

The reason I asked for advice was for a future build is going to contain massive storage resources. That dell T710 simply acts as a departmental server and research platform for our small group of research scientists and houses 8TB of data.

In the future I want to build out a storage machine that houses 20TB+. Like I said before there are lots of good cards with respect to perf, kernel drivers. But I would also like one that is easy to manage especially when the system is going to contain some 40-50 independent spindles.

Thanks for replying.
spookware

---

### Post by KiLaHuRtZ on 2010-01-27
Check out 3ware controllers.  I own 3 of them.  They are fully supported in the linux kernel, come with a nifty cli tool to manage.  I was even able to write my own nagios plugins off of it to alert me if a drive fails or if raid is rebuilding, initializing, verifying, etc. as well as provide with with percent completion.  They also support SNMP as well and you can purchase the optional backup battery unit for them.  Another cool feature is they support multicard raids.  You could go as extreme as dumping 6 cards in a server with 16 ports each and at 2TB disks you could create a 192TB raid 6 system!

---


---
title: "Ubutu Server 8.04 on HP Proliant DL160 G5"
date: 2008-05-01
forum: Server Platforms
---

### Post by stonehead on 2008-05-01
Hi all, I am planning to order an HP Proliant DL160 G5 as web server. However, the HP reseller told me that only Redhat & SUSE are supported, and, by using Ubuntu Server, they may not guarantee it works, especially RAID (SATA). Since this is my first HP unit and have no previous experience with HP, I need your feedback on whether Ubuntu Server 8.04 works on this machine.

From reading of other posts, I also notice there are some workaround to make Ubuntu/Debian recognizing the RAID controller, but some said speed are greatly reduced. Is it worth a try or simply go with other systems from IBM or Dell?

Many thanks...

SH

---

### Post by ghostknife on 2008-05-03
The problem with "servers being supported" is usually related to RAID, which is why they mentioned it.

The drivers are rarely open source, and the manufacturers only cover the major server distro's, ie. SuSE and Redhat EL.

When the drivers are compiled and built it is built against their libc and kernel versions. Newer version should run the drivers fine, but sometimes they refer directly to files in the server's filesystem layout. Which would require some hacking.

Also sometimes they are boot drivers (well, mostly always since it needs to be loaded during installation). Which makes it even more difficult as they don't recognize the other installation.

If you are willing to switch to RedHat, take a chance. If it doesn't work with Ubuntu, you can just switch. Also concider using CentOS, which is a free version of RedHat EL. I can't guarentee that it will work with CentOS though, but why it wouldn't work I don't know. Only reason why it wouldn't work is if the driver disk does a name check to see if the names match against it's support distros. But I doubt this. 

Regarding a performance decrease. This will only happen if some translation needs to be done. Like emulation of certain features it requires in these distros (like using custom kernel features, or scripts to emulate the distro's environment). This all depends on the driver, and most properly written drivers will work with any distro and won't give you a performance impact.

More I can't tell you, since I haven't worked with these servers, but some insight is all I wanted to give, so you can make a more informed decision.

Good luck and keep us updated!

---

### Post by vcbranco on 2008-05-04
This can help you

[http://h71028.www7.hp.com/enterprise/cache/433096-0-0-173-338.html?jumpid=reg_R1002_PTPT](http://h71028.www7.hp.com/enterprise/cache/433096-0-0-173-338.html?jumpid=reg_R1002_PTPT)

---

### Post by stonehead on 2008-05-06
Thank you ghostknife & vcbranco...

I am a Debian user for many years and Ubuntu since 6.06LTS. Moving to CentOS/RedHat/SUSE because of hardware problem is the last thing I want to do...  While HP has "unofficial" support for Debian (in terms of hardware), these so called supported hardware are mostly older or of higher end products such as its SmartArray line of RAID controllers. The RAID controller used in DL160 G5 (a low cost server) is SC40Ge SAS Host Bus Adapter with RAID. This controller is also used in ProLiant ML310 G5. So far I can't find any information on Debian/Ubuntu support for this RAID controller or these 2 servers. If someone can confirm it works with Ubuntu 8.04LTS or Debian Etch, then I am a happy man.:biggrin:

Another questions, in Ubuntu's [Validated Hardware page]("http://www.ubuntu.com/products/whatisubuntu/serveredition/validatedhardware"), to what level the "Compatible" rating is on hardware support, especially on RAID controller? For example, it says Dell PowerEdge 1950 is "Compatible", but why there are still a lot of workarounds needed to get the RAID controller working with Ubuntu, or having poor disk performance with those "Compatible" systems? This make me reluctant to just pick one from the list and install Ubuntu on it.:roll:

---

### Post by stonehead on 2008-05-06
Further browsing at HP's [IT Support Center]("http://forums12.itrc.hp.com/service/forums/categoryhome.do?categoryId=264") forum, it seems the RAID controller in DL160 G5 may as well be a software RAID controller, which, needs driver to make Linux into recognizing it as a RAID array. Without the driver, Linux sees 2 separate disks instead of one RAID array. As most of you already know, only RedHat & SUSE got drivers from HP.

So, there is no RAID 1 solution for DL 160 G5? :confused:

---

### Post by robvarga on 2008-05-06
> **stonehead said:**
> Further browsing at HP's [IT Support Center]("http://forums12.itrc.hp.com/service/forums/categoryhome.do?categoryId=264") forum, it seems the RAID controller in DL160 G5 may as well be a software RAID controller, which, needs driver to make Linux into recognizing it as a RAID array. Without the driver, Linux sees 2 separate disks instead of one RAID array. As most of you already know, only RedHat & SUSE got drivers from HP.

So, there is no RAID 1 solution for DL 160 G5? :confused:

If you can get Linux to see the two separate drives, you won. The Softraid/Hostraid/Fakeraid low-end solutions are in fact software raid running from the bios of the card, so it gives you no hardware assist. At that point you are better off using other ways of making Linux do RAID1 for you, and if you see the two drives as two independent devices, then you are able to do just that.


BR,

Robert

---


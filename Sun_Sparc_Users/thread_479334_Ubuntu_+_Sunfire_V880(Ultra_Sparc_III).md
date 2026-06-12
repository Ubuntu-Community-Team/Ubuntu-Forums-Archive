---
title: "Ubuntu + Sunfire V880(Ultra Sparc III)"
date: 2007-06-20
forum: Sun Sparc Users
---

### Post by MrKra on 2007-06-20
Hello,

Is it recommended to install Ubuntu Server on a Sunfire V880 (Ultra Sparc III)?
Im really not sure about this and cant find much about this with Google.

I have this Machine here which should work with some Linux Distribution as a Firewall in the future.

So Perhaps somebody here knows a little bit more than me?

Thx in advance.

---

### Post by netztier on 2007-06-20
> **MrKra said:**
> Hello,

Is it recommended to install Ubuntu Server on a Sunfire V880 (Ultra Sparc III)?
Im really not sure about this and cant find much about this with Google.

I have this Machine here which should work with some Linux Distribution as a Firewall in the future.

So Perhaps somebody here knows a little bit more than me?

Thx in advance.

Well.. the results I get when I enter "v880" into [http://lists.debian.org/google.html](http://lists.debian.org/google.html) are not too encouraging. And since Ubuntu is based on Debian, I fear that running Ubuntu on a V880 is going to be a daunting task.

BTW.. is that bound to be a multi-interface gigabit-performance monster firewall? a V880 for a Firewall, now that's something you wouldn't see everyday...

best regards

Marc

---

### Post by MrKra on 2007-06-21
Hello netztier,

maybe this sounds a little bit crazy but this machine is just standing around here with nothing to do.
Its a little bit oversized I think, its Job would be to act as a firewall for 5 networks with ~70 Clients.

Thx for your Link - I see big Problems arising.:D
So I will try it and post some results.

---

### Post by netztier on 2007-06-21
> **MrKra said:**
> maybe this sounds a little bit crazy but this machine is just standing around here with nothing to do. Its a little bit oversized I think, its Job would be to act as a firewall for 5 networks with ~70 Clients.

Well it's going to be ehm...  how shall I put this ... it will certainly be sufficient.

And as long as you can afford the electricity for powering it and cooling the room it is in - don't let anyone stop you :-)

Best regards

Marc.

---

### Post by mips on 2007-06-21
> **MrKra said:**
> 
Its a little bit oversized I think, its Job would be to act as a firewall for 5 networks with ~70 Clients.


If that is what you want it to do then why dont you use the most secure OS by default, OpenBSD. That in conjunction with pf (packet filter) & Firewall Builder would make an excellent firewall.

OpenBSD has even been tested on it,  [http://www.openbsd.org/sparc64.html](http://www.openbsd.org/sparc64.html)

---

### Post by MrKra on 2007-06-22
Seems like Ubuntu 7.04 won´t do it - Problems with the SILO Bootloader.
OpenBSD sounds like an interesting alternative, I will try it.

---

### Post by MrKra on 2007-06-29
OpenBSD was a bad choice, it only supports one CPU.

Im hopeless, t think I will never get any free Linux/Unix running on this.

---

### Post by mips on 2007-06-29
Sorry about that, this lead me to believe otherwise, [http://www.openbsd.org/faq/faq8.html#SMP](http://www.openbsd.org/faq/faq8.html#SMP)

Another option is FreeBSD which i'm 100% certain supports SMP.

---

### Post by netztier on 2007-06-29
> **mips said:**
> 
Another option is FreeBSD which i'm 100% certain supports SMP.

[COLOR="Red"][I]EDIT I BAH, FORGET MY POST. 
Shouldn't write posts while still being feverish :-/ NetBSB and FreeBSD are not the same things.
[/I][/COLOR]

But not the UltraSparc III CPU

[http://www.netbsd.org/ports/sparc64/](http://www.netbsd.org/ports/sparc64/) (see the list of unsupported hardware at the bottom of the page)

... and while we're at it - it doesn't seem to support SMP on sparc64 either (according to that list)

We're running out of options here... :-(

[COLOR="DarkGreen"]*Edit II: [http://www.freebsd.org/releases/6.2R/hardware-sparc64.html](http://www.freebsd.org/releases/6.2R/hardware-sparc64.html) bad luck with FreeBSD on the UltraSPARC III, too.*[/COLOR]

best regards

Marc

---

### Post by mips on 2007-07-01
> **netztier said:**
> [COLOR="Red"
We're running out of options here... :-(


Solaris 10 or Open Solaris ?

---

### Post by ykanello on 2007-07-06
Personally I wish I had hardware like that to try it...
i have tried ubuntu on v120, T1, and an E450. 
I never had serious issues except that at least one disk must be EMPTY (no partitions) for the installation of linux to start. 
I was getting a strange error if I would boot the linux CD with the solaris partitioned disk.
I read the threads about the v880 and debian and there is a person replying in that thread that he has a v440 booted with debian. 

Does the v880 have an ilom or a rsc card?
Are you getting the console from the card or the serial? I would have a doubts if the serial works all the way. 
How many cpu modules are installed? Are they active when you are in eeprom?

---

### Post by kelt65 on 2007-07-17
> **MrKra said:**
> Hello,

Is it recommended to install Ubuntu Server on a Sunfire V880 (Ultra Sparc III)?
Im really not sure about this and cant find much about this with Google.

I have this Machine here which should work with some Linux Distribution as a Firewall in the future.

So Perhaps somebody here knows a little bit more than me?

Thx in advance.

A V880? That's like an $40,000 box there, minimum. Using it as a firewall is a bit much, don't you think? Especially considering just having it on probably costs about $80 a month in power alone.

I would not run linux on such a thing, except as a lark.

---

### Post by rnz0 on 2007-07-22
HI, 
I got a v880 with 4 processors and 8gigs, an e450, several e250 and ultra5s. We are concerned about the v880. We want to go ubuntu server, Solaris 10 is not an option. Again, has anyone tried on the v880 succesfully?
thanks

---

### Post by ykanello on 2007-07-23
destroy the partition in the local disks that you will install, and try to boot. 
Please let us know too. 
I don't have a machine with sparc3, or more, so I cannot tell you.
It should boot no problem according to my experience, as long as there is no solaris partitioned disks.

---

### Post by rnz0 on 2007-07-23
Unfortunalely this big guy (the v880) runs all production stuff so we can't take chances. We will be shifting services and systems until we get to take it down. We will use different hdds and go for it. 
Man, this is so exiting!
thanks ubuntu 
:mrgreen:

---

### Post by Metalkhan on 2007-11-19
> **rnz0 said:**
> Unfortunately this big guy (the v880) runs all production stuff so we can't take chances. We will be shifting services and systems until we get to take it down. We will use different hdds and go for it. 
Man, this is so exiting!
thanks ubuntu 
:mrgreen:

Have you succeeded in installing ubuntu on the v880? I'm really interested on the version you used, problems you came across and how you overcame them. I'd like to try ubuntu on the SunFire v880 I have here sitting, doing nothing.

---

### Post by jcastill on 2007-11-21
I have a V880 yet it is in production with solaris 10 so I can't touch it. Yet the "owners" of the machine are interested in moving it to Ubuntu some day. So I'm also interested if you get it to work.

Thanks

Jose

---

### Post by rnz0 on 2008-03-02
Hi, 
I finally moved all production services out of my V880 and shut it down. I will start  installing Ubuntu.
First, need to make sure issues on it are resolved:
[[http://www.sunshack.org/data/sh/2.1/infoserver.central/data/syshbk/Systems/SunFire880/repair.html](http://www.sunshack.org/data/sh/2.1/infoserver.central/data/syshbk/Systems/SunFire880/repair.html)]("http://www.sunshack.org/data/sh/2.1/infoserver.central/data/syshbk/Systems/SunFire880/repair.html")
Patches at sunsolve site:
[http://onesearch.sun.com/search/onesearch/index.jsp?otf=ss&site=sunsolve&col=support-patches&rt=false&advanced=true&required=v880&cs=true&nh=10&rf=0&doctype=pdf%2Chtml%2Cxml%2Cplain&reslang=en&ssnf=false&arch=0&sstab=sscollection%3ABUG%2Csscollection%3ATECHNICALINSTRUCTION%2Csscollection%3APATCH%2Csscollection%3APATCHRPTS%2Csscollection%3ASUNALERTORACLE%2Curl%3Asunsolve.sun.com%2Fhandbook%2Csscollection%3APROBLEMRESOLUTION%2Csscollection%3ATROUBLESHOOTINGORACLE&qt=%2Bv880]("http://onesearch.sun.com/search/onesearch/index.jsp?otf=ss&site=sunsolve&col=support-patches&rt=false&advanced=true&required=v880&cs=true&nh=10&rf=0&doctype=pdf%2Chtml%2Cxml%2Cplain&reslang=en&ssnf=false&arch=0&sstab=sscollection%3ABUG%2Csscollection%3ATECHNICALINSTRUCTION%2Csscollection%3APATCH%2Csscollection%3APATCHRPTS%2Csscollection%3ASUNALERTORACLE%2Curl%3Asunsolve.sun.com%2Fhandbook%2Csscollection%3APROBLEMRESOLUTION%2Csscollection%3ATROUBLESHOOTINGORACLE&qt=%2Bv880")

Especially:
Hardware/PROM: Sun Fire V880 / V890 Flash PROM Update   
Patch Readme 121688-04
[http://sunsolve.sun.com/search/document.do?assetkey=1-21-121688-04-1](http://sunsolve.sun.com/search/document.do?assetkey=1-21-121688-04-1) - Aug 10, 2007
 
Hardware/PROM: Sun Fire V880 / V890 Flash PROM Update 
Patch Readme 119244-03
[http://sunsolve.sun.com/search/document.do?assetkey=1-21-119244-03-1](http://sunsolve.sun.com/search/document.do?assetkey=1-21-119244-03-1) - Jun 13, 2006
 
Hardware/PROM: Sun Fire V880 / V890 Flash PROM Update 
Patch Readme 119241-01
[http://sunsolve.sun.com/search/document.do?assetkey=1-21-119241-01-1](http://sunsolve.sun.com/search/document.do?assetkey=1-21-119241-01-1) - Sep 6, 2005
 
Hardware/PROM: Sun Fire V880 / V890 Flash PROM Update  
Patch Readme 119231-01
[http://sunsolve.sun.com/search/document.do?assetkey=1-21-119231-01-1](http://sunsolve.sun.com/search/document.do?assetkey=1-21-119231-01-1) - Jun 16, 2005

[ Sun Fire 880 & 890 Fibre-Channel Backplane Firmware patch]("http://sunsolve.sun.com/search/document.do?assetkey=1-21-117814-01-1")

---

### Post by rnz0 on 2008-03-06
Update:

TOTALLY UNSUCCESSFUL!

I got this bug:
[https://launchpad.net/ubuntu/+source/silo/+bug/40119](https://launchpad.net/ubuntu/+source/silo/+bug/40119)

After cold restart, and setting cdrom as boot device, I try to install but hangs at:
Booting linux...

To my dismay gentoo fails booting linux too. They have a special kernel version for it and everyone claims it works. It doesn't work for me. 

[http://www.gentoo.org/proj/en/base/sparc/sunhw.xml](http://www.gentoo.org/proj/en/base/sparc/sunhw.xml)

Of course Solaris 10 was flawless and I am sold on ZFS and linux containers :/

Sorry guys. I really wanted Ubuntu to work on this machine but my time is over and my bosses are waiting to put it back online.

---


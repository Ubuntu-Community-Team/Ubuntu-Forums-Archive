---
title: "Ubuntu server compatibility with server hardware"
date: 2009-05-23
forum: Server Platforms
---

### Post by televisi on 2009-05-23
HI All,
I'm planning to create PC server using Ubuntu Server edition.

I visit some of the hardware/manufacturer site and most of them don't include Ubuntu O/S as their compatible software.

For instance, this RAID hardware [[COLOR="Red"](Click Here)[/COLOR]]("http://ask.adaptec.com/scripts/adaptec_tic.cfg/php.exe/enduser/std_adp.php?p_faqid=15316"), only list below OS:
```
Microsoft Windows Server 2008 Standard 
Microsoft Windows Server 2008 Enterprise 
Microsoft Windows Server 2008 Datacenter 
Microsoft Windows Vista Ultimate x86 
Microsoft Windows Vista Ultimate x64 Edition 
Microsoft Windows Vista Home Premium x86 
Microsoft Windows Vista Home Premium x64 Edition 
Microsoft Windows Vista Home Basic x86 
Microsoft Windows Vista Home Basic x64 Edition 
Microsoft Windows Vista Business x86 
Microsoft Windows Vista Business x64 Edition 
Microsoft Windows Server 2003 x64 Edition 
Microsoft Windows Server 2003 Standard Edition 
Microsoft Windows Server 2003 Enterprise Edition 
Microsoft Windows Server 2003 Web Edition 
Microsoft Windows XP Professional x64 Edition 
Microsoft Windows XP Home Edition 
Microsoft Windows XP Professional 
Microsoft Windows 2000 
Red Hat Enterprise Linux 5 
Red Hat Enterprise Linux 4 
SuSE Linux Enterprise Server 10 
SuSE Linux Enterprise Server 9 
SCO UnixWare 7.1.4 
SCO OpenServer 6.0 
Sun Solaris 10 (x86) 
Sun Solaris 10 (x64) 
FreeBSD 6.2 
FreeBSD 6.1 
FreeBSD 5.4 

```

Will this be a problem once I build them?

---

### Post by koenn on 2009-05-23
It might be.
You'll need a driver ('module') that allows your operating system (kernel) to interact with the hardware. As the site states, the vendor will provide a driver for the listed operating systems - and ubuntu isn't one of them.

You may find that the open source community has developed its own set of drivers for this piece of hw (check e.g. [http://www.ubuntuhcl.org/browse/search+adaptec?manufacturer=11](http://www.ubuntuhcl.org/browse/search+adaptec?manufacturer=11) or [http://man.sourcentral.org/debian-unstable/4+aac](http://man.sourcentral.org/debian-unstable/4+aac) ) and maybe you'll even find them packaged in the debian or ubuntu repos, so you're be able to use this controller, but in case of failure to get it working, or problems later on, you can't rely on the vendor to help you out. 

So, it's your call ...

---

### Post by televisi on 2009-05-24
Hm... interesting...
The reason I asked this question is, I was thinking to buy RAID 5 hardware for my backup. 

As you might already notice, I'm new in this RAID backup thingy, so far I've been able to backup my data using RSYNC, but I don't think that is enough (does it?)

I also heard that in Ubuntu, we can use RAID software-type, instead of using hardware one. Do you think it worth of try? (compare with buying expensive RAID hardware which we are not even sure whether it is working in Ubuntu / not)

What do you think?
Thanks

---

### Post by koenn on 2009-05-24
re backups:

RAID and backups are separate things, and should be treated as such. 
a RAID configuration allows you to combine multiple disks, with several effects depending on what RAID conf you choose. The most common reason to do RAID is that your system remains operational and its data available in the event that 1 (or more) disks die. So it's a matter of availability.

Backups let you restore data in all sorts of events (disk died, unintentional delete, complex script got messed up while trying to improve it,  database got corrupted due to act of god,  ... ), but may takes considerable time, and there's usually a difference between the system in its current state, and the most recent backup.

In a production environment, you do both. For home use : it depends on how you value your data and your time, and how well you can afford to be without a PC for a couple of hours/days/....


re software raid. 
I have my doubts about it. I find it strange that a raid would depend on software in an OS that resides on that RAID, so I wouldn't use it for the actual system. Data ? maybe. Home users do it, but in a corporate environment people look for hardware raid (on servers / storage appliances- pc's aren't worth the trouble/cost)

There are some software RAID vs. hardware RAID discussions on these forums, maybe you want to do a search for them.

---


---
title: "Dell software raid"
date: 2011-02-23
forum: Server Platforms
---

### Post by dodgyphil on 2011-02-23
Hi,

Hi was looking at replacing an old Microsoft Small Buisness Server 2000 with an Ubuntu system.

I was looking at the following Dell system:-

[http://configure.ap.dell.com/dellstore/config.aspx?oc=t420901au&c=au&l=en&s=bsd&cs=aubsd1&model_id=poweredge-t310](http://configure.ap.dell.com/dellstore/config.aspx?oc=t420901au&c=au&l=en&s=bsd&cs=aubsd1&model_id=poweredge-t310)

I was concerned about the "Embedded software Raid" and if Ubuntu will work with it?

The system is fairly basic:-

We want a server with 2 x 500g SATA hard drives mirrored.
We need to connect 8 Windows computers logged into a business domain. Accessing mail and a Microsoft Access data base.

If any one has advice on best hardware configuration it will be greatly appreciated.

Cheers

Phil D

---

### Post by Vegan on 2011-02-23
Steer clear of software RAID, you are on the road to disaster.

Use JBOD or get a card

read this

[http://www.windows-it.tk/papers/raid.php](http://www.windows-it.tk/papers/raid.php)

---

### Post by YesWeCan on 2011-02-23
That was weird.

> **dodgyphil said:**
> I was concerned about the "Embedded software Raid" and if Ubuntu will work with it?
Regarding the raid, Yes. You just disable bios raid. Ubuntu does its raid on its own. You had better check with Dell that it is just fakeraid and can be disabled.

---

### Post by dtfinch on 2011-02-24
Since you mentioned Access I'd suggest looking at the [veto oplock files](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/locking.html#id2616903) option in Samba to disable oplocks (used by Windows' network file caching) for .mdb files, when you do get it set up.

If you use Active Directory, and the SBS 2000 server is also your domain controller, I'd be cautious about replacing it with Samba 3, though I have no direct experience with migrating domains or setting up a Samba PDC.

---

### Post by dodgyphil on 2011-02-24
Hi All,

Thanks, very helpfull. Sounds like I'd be better of with out a "Embedded Software Raid" and let Ubuntu do it's own things. Or get a dedicated card.

Also thanks for the heads up on MS Access. Has been my intention to export the tables and do something in SQL. Never have time so unfortunatly stuck with MS Access for now.

I'm sure I'll call on your good advice again once I start the installation.

Cheers

Phil D

---


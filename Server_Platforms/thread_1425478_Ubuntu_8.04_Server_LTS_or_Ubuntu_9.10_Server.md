---
title: "Ubuntu 8.04 Server LTS or Ubuntu 9.10 Server"
date: 2010-03-09
forum: Server Platforms
---

### Post by pungki on 2010-03-09
I have a project to create a server using Ubuntu. I found that Ubuntu 10.04 is coming out. But the project is time sensitive. So I have to choose the OS soon. 

The server will be used as a hosting server of virtual school, using Moodle. 5 users (max) are able to virtual desktop to the server simultaneously. 

Based on that, which distribution should I use? Ubuntu Server 8.04 LTS or Ubuntu Server 9.10 ?

And, does anyone has suggestion what kind of hardware specification for the server?

Thank you in advance.


-Pungki

---

### Post by jarilin on 2010-03-09
My choice would be 9.10.
Since it's much smaller update to 10.04, than 8.04 -> 10.04.
Then there is not so much major version updates in servers programs.

---

### Post by spynappels on 2010-03-09
IMHO it depends on whether you want stability or cutting edge features. For production servers I always use LTS releases, but for testing and projects I would use a recent build, where bugs would not be a huge problem.

It also depends on how comfortable you are debugging and how happy you are to fix problems yourself, and how much time you can afford to spend tinkering.

I personally tend to run several VMs for each application, a stable LTS release for the production system and a recent release with the same application for testing. Where practical, I mirror the application data, so I can compare how the application works on recent amd LTS and then I decide if I am happy to take the plunge and deploy the recent release as the production server.

---

### Post by denver on 2010-03-09
I would go for 8.04 as well. It's been tried and tested, and you can use it for another 3 years before you actually need to upgrade. Its a server after all, and your main focus should be stability.

With LTS builds, you get what you expect. Intermediary builds tend to give you surprises. But as spynappels already said, if you just want to test things and don't mind things going terribly wrong, 9.10 is the way to go.

Distribution upgrades take the same time regardless of what version you are upgrading from (8.04 or 9.10).

---

### Post by NullHead on 2010-03-09
Between the two servers I run, ubuntu 9.10 has been more than stable enough. I've encountered zero bugs, and the stability has been great. 

Granted, these servers aren't considered "production" servers that require 100% uptime, but for my usages, it's been wonderful. 

I suggest Ubuntu 9.10.

---

### Post by pungki on 2010-03-09
Thank you for quick reply.

Requirement of the server are :

[LIST]
[*]a load of 160 users for Moodle/Mahara in total, but a maximum of only 40 simultaneous users during peak times
[*]while testing, a maximum of 5 simultaneous users of a virtualised desktop and client applications
[*]less than 1000 page hits per day on our websites (not including Moodle/Mahara), but this could peak at 120 page hits per hour at peak times
[/LIST]

And the software should be :
[LIST]
[*]Ubuntu Linux Server Edition incl. the latest Firefox
[*]Apache Web Server with PHP module
[*]A proxy server set up with a large cache for accessing international sites
[*]Antivirus/malware product (maybe ESET Gateway Server Security)
[*]PostgreSQL  (instead of MySQL because Mahara prefers it and Moodle supports it)
[*]A Remote Access solution both for server administration and also multiple virtual user login via a VPN from a thin client ([X2GO]("http://www.x2go.org/index.php?id=4"))
[*]Multi-purpose File Compression/Decompression  Utility
[*]Adobe Acrobat Reader
[*]A Download Manager/accelerator/scheduler
[*]An FTP Client
[*]Open Office (full install which is available to schools)
[*]A couple of Media Players to support various formats (maybe mplayer and adobe flash player)
[*]Joomla
[*]Moodle
[*]LAMS and LAMS Plug-in for Moodle
[*]Mahara
[*]2 Websites and they are using Joomla for content management
[/LIST]


I found that ebox platform is based on Ubuntu 8.04. So I think I will try to use it.

One more question, please tell me if I put this in wrong thread.
I try to build the system under [this specification]("http://www.bhinneka.com/products/sku00010426/extron_netsystem_a100__(s344).aspx") plus 2 GB RAM (Total 4 GB RAM) and 500GB x 3 (2 is set to be RAID 0 stripping and 1 independent for backup). Is it adequate for requirement above?

Thank you.


-Pungki

---


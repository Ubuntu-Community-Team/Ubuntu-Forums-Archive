---
title: "Raid 1 setup on Ubuntu server"
date: 2012-02-20
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2012-02-20
Hi

Would like to install Ubuntu Server 11.04 on a Fujitsu Siemens PRIMERGY Econel 50 Server, 
[http://www.fujitsu.com/downloads/TW/services/server/ntprimergy/pdf/0606/ds_prim_econel50_en.pdf]("http://www.fujitsu.com/downloads/TW/services/server/ntprimergy/pdf/0606/ds_prim_econel50_en.pdf"),
using 2 x 160GB hard drives.

Already happily running Ubuntu Server 11.04 on another computer, but have no experience of RAID.

Would appreciate guidance as to best way of proceeeding?

TIA

---

### Post by a2j on 2012-02-20
software, fake, or hardware raid?

---

### Post by ChrisRChamberlain on 2012-02-22
a2j

Thanks for your reply - been waiting to receive server.

According to the manual > The server is equipped with a built-in SATA controller with software RAID 0/1/10 functionality. The
software RAID is configured automatically during system startup. Up to four hard disk drives may be
operated by the controller. Depending on the number of disk drives attached, either a RAID 0 (with
one drive) or a RAID 1 (with two drives) is configured automatically.So would Ubuntu recognise this configuration?

---

### Post by zeljkojagust on 2012-02-22
Hmmm.... software RAID controller. In my experience it will be a pain in the a..! I do not wish to scare you, but you will probably have to try several versions of firmware before a controller will be visible inside OS and it will probably work only in some strange JBOD mode. My suggestion is to skip RAID configuration on the controller and configure a software RAID inside Ubuntu installation process. If you need to know how, be free to ask.

---

### Post by Bradyhawke on 2012-02-22
I second what zeljkojagust said - been working with Linux/Ubuntu for over a year now and have done 3 installs with server boards that had built-in RAID controllers (all software-based).  The configuration was a bit of a pain for me that in the end it was so much simpler to just install the software RAID during the Ubuntu o/s installation process.

Just for the record, 2 of the server installs were RAID 1 Arrays each with 2 x 320GB HDDs and the 3rd was a RAID 5 array of 4 x 640GB HDDs.  I've replaced a single 640GB HDD so far (but that HDD was VERY used), otherwise everything has been running smooth for almost  a full year on them.


:guitar: - bradyhawke

---

### Post by idef1x on 2012-02-22
Besides the sata controllers software RAID being a pain in the a.. keep in mind that if you would use that and your sata controller would fail....then trying to get access to your data would be more then just a pain in the... 

I would go for software RAID in Ubuntu as well. Performance would most likely be the same as for the other software based solution, but at least the way the RAID is configured stays the same if you need to move it to another system or whatever...(think about rescue CD/USB with ubuntu RAID support)...

---

### Post by ChrisRChamberlain on 2012-02-22
zeljkojagust, Bradyhawke, idef1x

Thank you all for your replies, content of which has been noted.

As a first step, will put a spare single drive into the server and install Ubuntu Server 11.04 without using any Fujitsu Siemens startup discs, etc.

This will enable any driver issues to be resolved.

Assuming all is well, will then replace the temporary drive with 2 x 160GB drives and start again.

At that time, will mark this thread as 'Solved' and start a new thread requesting guidance through the installation process.

Any comments on this proposal would be welcome.

---

### Post by a2j on 2012-02-22
I would not use on-board sata fake raid. either software raid (mdadm) or hardware raid, if willing to put your hopes on a single controller.

---


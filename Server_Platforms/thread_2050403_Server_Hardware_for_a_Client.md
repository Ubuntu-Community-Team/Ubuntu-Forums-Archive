---
title: "Server Hardware for a Client"
date: 2012-08-30
forum: Server Platforms
---

### Post by gyzer on 2012-08-30
I am looking into pricing for possibly setting up an Ubuntu server for a client of mine.

Are there any OEM server manufacturers out there that would be good to buy from? This is going to be mainly a file server for a couple of users. A Windows Server for them doesn't make much sense and I don't like the backup solutions that most NASes are compatible with. 

Any help or suggestions would be greatly appreciated.

---

### Post by gyzer on 2012-08-30
Any comments on System76.com?

---

### Post by sandyd on 2012-08-31
Heres a list of compatible server hardware (tested) [http://www.ubuntu.com/certification/server/](http://www.ubuntu.com/certification/server/)

And a list of compatible desktop hardware (tested) [http://www.ubuntu.com/certification/desktop/](http://www.ubuntu.com/certification/desktop/)

For a NFS file server, I would just go with freeNAS, or actually get a NAS.

---

### Post by gyzer on 2012-08-31
Thank you but I've seen those lists. 

I have looked at just getting a NAS but the issue I have is with off-site backups. Most of the options I've seen are for very expensive services.

From what I've seen from System76 is they have a pretty good warranty for hardware replacement.

---

### Post by sandyd on 2012-08-31
All manufacturers have a hardware replacement warranty. You can just RMA it, and ship them the unit.

If you get Enterprise HW, like the HP Blades, those will have extended and fast-repair warranties that will allow them to ship out replacement hardware immediately.

---

### Post by gyzer on 2012-08-31
So then are you saying I should buy from System76?

---

### Post by SeijiSensei on 2012-08-31
I've bought quite a few servers from Dell.  They have always worked well with Linux, and they ship with no operating system, so you're not paying a "Windows tax."

If you want to maximize uptime, then I'd suggest a machine with "hot-swap" drives and redundant power supplies.  Also make sure you install a UPS.  APCs work well with Linux since you can use the [apcupsd]("https://help.ubuntu.com/community/apcupsd") monitoring daemon.  Here's a [good choice for a single server]("http://www.newegg.com/Product/Product.aspx?Item=N82E16842101381").

If hot-swap drives are too expensive, then make sure you have at least two hard drives in a RAID1 setup.  You can buy a hardware RAID card; the PERC/SAS devices in Dells are well-supported in Linux.  Alternatively you can use Linux software RAID with simply a pair of SATA drives.  I built a machine with these some months back and both Ubuntu Server 12.04 and CentOS 6.2 detected the RAID card and installed the correct driver.  I generally use CentOS on servers because some of the software I use, particularly [MailScanner]("http://www.mailscanner.info/"), is well-packaged for RedHat-flavored systems.

Here's [a machine to consider]("http://configure.us.dell.com/dellstore/config.aspx?oc=bedwkr1&model_id=poweredge-t310&c=us&l=en&s=bsd&cs=04").  It has 2 1TB hard drives (no HW RAID), a Xeon, and 4 GB of memory.  The price includes 3 years of warranty service including next-business-day onsite repairs.

---

### Post by gyzer on 2012-08-31
SeijiSensei - Thank you for the reply

I am a Dell guy when it comes to Windows. 99% of my customers run Dell workstations and server. The T310 is my go-to server for any low end setup, mainly because it has hot-swap drives and you can get it with dual power supplies.

The thing I'm a bit worried about with buying from Dell is that is everything going to work, hardware wise with 12.04 LTS? Also when it comes to warranty replacements, because I'm running a OS that it wasn't shipped with, will it be a big pain to prove to them something isn't work to get the replacement parts?

Hot-swappable isn't that big of a deal with this client, only going to do a RAID 1. 

Comparing that to the System76 [base server]("https://www.system76.com/servers/model/elav4") really makes it a no brainier even with a redundant power supply and upping the warranty to include the SATA drives.

My only issue is still, will the T310 work 100% flawlessly with 12.04 LTS?

---

### Post by gyzer on 2012-08-31
Just found out that the T310 is Ubuntu Certified for 10.04.4 LTS. I really want to make sure it runs on 12.04 LTS though.

---

### Post by sandyd on 2012-08-31
Should work for 12.04 if its compatible with older versions.

There might only be a few small problems, mainly to do with depreciation.

---

### Post by lykwydchykyn on 2012-08-31
> **SeijiSensei said:**
> the PERC/SAS devices in Dells are well-supported in Linux.  

Last time I got a server from Dell, I had to go through three RAID controllers before they sent me one that was compatible with Linux.  I think I ended up having to do software RAID in the end, too.

They do have Linux-compatible hardware, but make sure you're asking specifically for it, and research the RAID hardware they're proposing to include.

---

### Post by rubylaser on 2012-08-31
As SeijiSensei said, if you buy a PERC or SAS device they'll work fine in Linux.  The cheaper cards that Dell includes in their lower end servers are almost all fakeraid and should be avoided.

---

### Post by gyzer on 2012-08-31
I've had to deal with a cheap Dell T110 with a degraded array and it was setup using the on-board fake raid (wasn't setup by my company, was setup by their previous IT people). I talked with Dell and found that there were no linux drivers for the fake raid and we were screwed.

I'm really liking the idea of the T310 with two SATA drives using software RAID. This is only going to be a file server for a few people so performance isn't an issue.

Should I call sales at Dell and talk with them with what I want to do? I can't have my client purchase a server and then having something major happen with running Ubuntu and have it not be 100% compatible.

---

### Post by SeijiSensei on 2012-08-31
I really don't think you need to worry.  Dell servers are pretty much plain-vanilla boxes with no arcane parts.  Most of them have Intel or Broadcom Ethernet, standard SATA drives, and Intel or Matrox VGA graphics.  

As I said I've been installing Dells as Linux servers for a long time.  I started using i386 Dimension boxes back in the mid-1990s.  My most recent purchase for a client was an R410 rack server with dual Xeons, dual Broadcom NICs, a SAS1068E RAID controller, and a Matrox MGA G200eW WPCM450 video adapter.  Both Ubuntu 12.04 server and CentOS 6.2 installed cleanly on this box.

There are many fewer differences between versions when it comes to servers and server software.  Most of the changes are happening on the desktop.  I'd be surprised if a box that was certified for 10.04 will have any problems with 12.04.  If you were using fancy graphics or high-end sound cards or an unusual wifi device you might have a compatibility issue.  On a server, compatibility problems are highly unlikely.  I'd be more concerned about printer drivers to be honest, and even more concerned if you wanted to run a scanner.  But those issues concern the peripherals themselves, not the server.

---

### Post by gyzer on 2012-08-31
SeijiSensei, you are definitely building confidence in me with doing this. I really appreciate it.

We have a Dell rep that we deal with. I'm going to give him a call on Tuesday.

This is going to be the first Ubuntu Server deployed by my company. Also this has been a client that's been with us for almost 10 years. We stand behind our decisions, and the last thing I want is for us to screw up on this and have an unhappy client, or one who trusts us less.

Again, thank you all for your help. I really appreciate it.

---

### Post by gyzer on 2012-08-31
Thanks again everyone

---


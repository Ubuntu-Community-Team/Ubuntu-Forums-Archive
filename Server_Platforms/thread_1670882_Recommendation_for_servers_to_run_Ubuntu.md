---
title: "Recommendation for servers to run Ubuntu?"
date: 2011-01-19
forum: Server Platforms
---

### Post by m00dawg on 2011-01-19
Hi all!

I have finished a proof of concept for using Ubuntu as our OpenLDAP/file-server for our Windows and OS X environment and am to the point of spec'ing out the hardware. I am looking for a rackmount solution and found some good options from HP and Cisco.

I was curious if anyone had any recommendations on server vendors that have good hardware support for Ubuntu? I assumed it would be similar to RHEL and that the open source drivers were supported via a heavily modularized kernel. No biggie there, but if I had to load in custom drivers for things like a RAID controller, I wanted to find a vendor that was more Ubuntu friendly. I don't want to have to be compiling kernels and diddling with customer drivers, for instance.

If I had any preferences, they would be for 3.5" drive form factors, Opteron CPUs (though not really a significant thing) and would be more for the entry-level side of things. We don't need a monster 3U drive server for or tiny network. A 1U or 2U would be fine generally.

Thanks!

---

### Post by koenn on 2011-01-19
In Belgium, HP DL360 - 380 and the likes are popular as a general purpose "work horse" server, both for Windows and Linux or as host for VMware ESX and such. I got Debian running on a couple of those with default kernels and all hardware detected and supported ootb, I'm guessing Ubuntu would be no problem either. 

They come as towers and 2U rack mountable

---

### Post by m00dawg on 2011-01-19
That's good to know! My favorite pick is the HP DL180. The price point is right and it has enough expansion capability for us, etc. I assume its parts would also work on a base kernel if it worked on the DL360.

It's shame more vendors don't support Ubuntu Server officially though :/

---

### Post by snowpine on 2011-01-19
Have you seen this page?

[http://webapps.ubuntu.com/certification/](http://webapps.ubuntu.com/certification/)

---

### Post by m00dawg on 2011-01-19
No, but that's fantastic! Indeed the DL180 is on there. Problem solved there, sweet!

Doesn't solve the problem of HP supporting Ubuntu but, meh, as long as they still support the hardware it's basically a non-issue.

Thank you very much!

---

### Post by tgalati4 on 2011-01-19
duplicate post.

---

### Post by tgalati4 on 2011-01-19
I bought a couple of dell poweredge 1750's for $300 each.  Dual Xeon dual-core 2.8 GHz (4 cores total), 4 GB RAM, 3 scsi disks.  Run hardy fine and someone was kind enough to recompile OMSA (dell's web-based hardware manager) from Redhat to debian.  They are power hogs though (240 watts when pressed, so be mindful if you are using them at home 24/7.  The machines have fallen out of warranty (5-years with extensions), but at that price, they are disposable.

They are not ubuntu certified (1950 and newer series) and they are only 32-bit architecture, but for a server, the web pages look just the same.

---

### Post by spynappels on 2011-01-20
I've just been speccing servers for a highly available web-app with mammoth storage, and have settled on HP ProLiant DL320 G6 with 4 hotswap SATA drives. The iLO (remote management) port is very helpful too as it gives a remote console plus power-cycle capabilities so ideal for a remote datacentre.

---

### Post by m00dawg on 2011-01-20
I have used ILO with HP's before. They may look utilitarian but HP makes some pretty awesome servers if you're going brand name.

---


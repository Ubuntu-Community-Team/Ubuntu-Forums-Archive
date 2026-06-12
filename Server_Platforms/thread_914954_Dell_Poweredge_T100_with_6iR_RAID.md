---
title: "Dell Poweredge T100 with 6i/R RAID"
date: 2008-09-09
forum: Server Platforms
---

### Post by monquixote on 2008-09-09
Hello All 

I'm just about to buy a Dell T100 with a 6iR RAID controller and a couple of SATA disks which I'm planning to run as a RAID 1 mirrored pair.
see here for server specs: [http://www.dell.com/content/products/productdetails.aspx/server-poweredge-t100?c=us&cs=555&l=en&s=biz](http://www.dell.com/content/products/productdetails.aspx/server-poweredge-t100?c=us&cs=555&l=en&s=biz)

Ideally I would like to use Ubuntu 8.04LTS Server, but I have some concerns about the RAID controller working after reading threads like this one: [http://ubuntuforums.org/showthread.php?t=719556&highlight=poweredge](http://ubuntuforums.org/showthread.php?t=719556&highlight=poweredge)

What I would like to ask is does anyone out there have any experience using this machine with Ubuntu?

I would especially like to know if I am likely to have problems with the RAID array as it is just going to be a DEV machine so I could build it with a single disk and forget about the RAID.

---

### Post by qwertzqwertz on 2008-11-05
FYI - Just received a PowerEdge T100 w/ SAS6iR controller and two 80GB SATA drives in RAID 1 configuration.  Worked great!

I installed 8.04.1 LTS server on it with no problems whatsoever.  There is no direct monitoring of the RAID from Ubuntu that I can see, but other than that, it seems fine.

I have not tried the Dell OpenManage stuff mentioned in the other post you pointed to.  I may try that in the next little while, but for now, I'm happy with it as is.  You can test the array by rebooting and going into the LSI monitoring stuff during the boot process (like going into BIOS setup).

- James

---


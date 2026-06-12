---
title: "Slow write speed with LTO-4 tape drive"
date: 2009-04-03
forum: Server Platforms
---

### Post by shizakapayou on 2009-04-03
I have an LTO-4 autochanger tape drive, specifically a Quantum Superloader 3.  It's connected to a Dell PowerEdge 2950, using a PCI-Express x8 SAS 5/e card: [http://accessories.us.dell.com/sna/products/Networking_Communication/productdetail.aspx?c=us&l=en&s=bsd&cs=04&sku=310-8285&~lt=popup&~ck=TopSellers](http://accessories.us.dell.com/sna/products/Networking_Communication/productdetail.aspx?c=us&l=en&s=bsd&cs=04&sku=310-8285&~lt=popup&~ck=TopSellers)

According to the Quantum pages: [http://www.quantum.com/ServiceandSupport/SoftwareandDocumentationDownloads/SuperLoader3/Index.aspx](http://www.quantum.com/ServiceandSupport/SoftwareandDocumentationDownloads/SuperLoader3/Index.aspx), I should be seeing around 430GB/hr.  At present, I'm getting closer to 130.  Quantum support has verified for me that the SAS 5/e is on the hardware compatibility list, and they've seen much better performance from it.  However, they've never worked with Ubuntu, and probably not anything but Red Hat, so they've been a bit useless for my situation.

They did want me to try a tool called hptapeperf, seen here: [http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=12169&prodSeriesId=254621&prodNameId=257848&swEnvOID=230&swLang=8&mode=2&taskId=135&swItem=co-11013-1](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=12169&prodSeriesId=254621&prodNameId=257848&swEnvOID=230&swLang=8&mode=2&taskId=135&swItem=co-11013-1)  However, I wasn't able to get it to work.  Any clues for getting it running?

Backup software is Bacula 2.44, compiled from source.  Server is on Server 8.04.2 64-bit.  I'm open to any ideas, not just about the HP tool.

---

### Post by Cheesemill on 2009-04-03
In my experience it is **very** rare to achieve maximum quoted data transfer speeds to a tape drive.  The speed you quote equates to roughly 120MB/sec which is beyond the transfer speeds of single hard drives.  The only way to shift this much data to the tape drive would be to use certain types of RAID.

This is assuming that your backup source is a local source, if you are backing up across a network then speeds would be much lower unless you are using a disk to disk to tape backup strategy.

Cheesemill

PS You could try using hdparm to measure your hard drive read speed to see if that is the limiting factor.

---


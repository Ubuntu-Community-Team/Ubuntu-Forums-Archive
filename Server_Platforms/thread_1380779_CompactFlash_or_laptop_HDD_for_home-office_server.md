---
title: "CompactFlash or laptop HDD for home-office server?"
date: 2010-01-14
forum: Server Platforms
---

### Post by dookka on 2010-01-14
My mini-itx server has two 3.5" HDDs in RAID 1, running Ubuntu Server 8.04.

I want to add another drive mainly to separate the OS from the data, but also to get some noise and power savings by using a low-power drive and allowing the big drives to spin down at least overnight.

My root partition uses 1.6GB with the data in other partitions; I have two free IDE interfaces but no SATA and no room for a third 3.5" HDD.

I figure for the same price, AU$65, I can get either a 160GB 2.5" IDE HDD or a 4GB Compact Flash (266x SLC) plus CF-IDE adapter.  The cool kids are going for SSD these days but as I don't run with the cool kids I thought I'd ask here:

Is CompactFlash acceptable for running a 24/7 Hardy server?
Or am I better off with a laptop HDD and gaining some extra GBs?

(I may update to Lucid when the time comes, but I'd have to move some services to a Hardy VM so I haven't made up my mind.)

---

### Post by tgalati4 on 2010-01-22
I would not trust a CF card for running a 24/7 server.  The continuous writing of log files would wear out the card.  Also, the flash-write controller will slow down over time as the uptime increases (attempting to level the write-wear across the card).

You would get better reliablity from a WD raptor or scorpio disk drive--not to mention speed.

I don't think spin-down and RAID1 are compatible--others will have to chime in with hands-on experience on this one.

---

### Post by CharlesA on 2010-01-22
I agree with the spin down thing. While it would save electricity, the contstant, power up/power down will wear out the disks faster then just leaving them spinning all the time.

---

### Post by David.Johnson on 2010-01-22
Go with the HD. As stated, the Flash drive will wear out with the constant writing. I just built a server with an external USB HD - works beautifully & my 1TB drive array won't suffer from some stupid mistake I may make :-)

---

### Post by HermanAB on 2010-01-23
Howdy,

If you use a HDD, then you can use hdparm to set the spin-down timeout to 5 minutes or so.

Whether you use a hdd or a flash disk, you have to stop the syslog daemon to prevent the constant writing of log files which will keep things from spinning down.

BTW, a modern flash disk won't wear out in your life-time even if syslog is constantly writing, but it may break - so give it a rest.

---

### Post by theozzlives on 2010-01-23
I tend to say good old fashion HDD. I'm still waiting to see how a SSD holds up in the long haul (besides the size I want is over $600.00, US). Flash should not even be an option.

---


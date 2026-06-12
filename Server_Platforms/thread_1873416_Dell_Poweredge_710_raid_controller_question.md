---
title: "Dell Poweredge 710 raid controller question"
date: 2011-11-01
forum: Server Platforms
---

### Post by djtopper on 2011-11-01
I plan on setting up a new 710 with RAID 1 using the default built in controller (attached).  I'm already pretty much at max budget for the machine (2 x 6core Xeons, 10Gb network, dual PSU) as it will spend its life routing TCP packets via a java (and later C++) server that I've written and have been testing on some older hardware for a while.  So for me, threads and bandwidth are the primary considerations.

But I've been reading about "fake raid" and whatnot.  But the Dell literature seems to clearly state that this is hardware raid.  I'm just curious if anyone has had some experience with them (eg., the default SAS 6/ir RAID controller).  In theory I could upgrade to the H200 or H700 based controller but at this point I'd rather not.

Thanks,

D

---

### Post by jacob.air on 2011-11-01
Just finished dealing with this myself. The answer I got was the PERC 5/6 (6 is the only one still made) is fully certified and the H200/700/800 is nearly there with some minor issues remaining with ext4. I chose the PERC 6/i SAS and during installation Ubuntu 11.04 detected the raid 10 volume configured in the hardware controller immediately.

---

### Post by djtopper on 2011-11-01
Right, but there's two options listed for HD controllers.

1.  SAS 6/iR Integrated, x6 Chassis

and

2.  PERC 6/i SAS RAID Controller, 2x4 Connectors, Internal, PCIe,256MB Cache,x6 

It seems clear that the first one is NOT a RAID controller.  The second is.

When you select RAID on the Dell website it DOES NOT automatically select a raid controller.  It defaults to the regular SAS 6/iR controller which I'm 99% sure means software RAID.

The Dell selector should at least trigger a warning about this, or some kind of note.

---

### Post by jacob.air on 2011-11-01
From what I've seen and read the PERC 6/i is a add-on card raid controller capable of more types of raid with better hardware capabilities. The SAS 6/ir seems to be either integrated or add-on but is limited to simple hardware raid configs including RAID 0 and 1. I could be wrong about that, but that is what a few answered questions on dells website suggest.

[http://lists.us.dell.com/pipermail/linux-poweredge/2008-July/036824.html]("http://lists.us.dell.com/pipermail/linux-poweredge/2008-July/036824.html")

Also, this page has a table that lists the RAID types and controller capabilities.

[http://www.dell.com/content/topics/topic.aspx/global/products/pvaul/topics/en/us/raid_controller?c=us&l=en&cs=555]("http://www.dell.com/content/topics/topic.aspx/global/products/pvaul/topics/en/us/raid_controller?c=us&l=en&cs=555")

Other than that, all I can say is the PERC 6/i works fine with the hardware raid setup I have. When asking this question originally the answer I got was the PERC 5 and 6 series (not sure if that includes the SAS 6/ir) are fully certified, while the PERC H-series controllers are nearly certified. 
The only people who seem to know this info are Canonical. So it doesn't look like the SAS 6/ir is a software raid controller, but that is just a very basic hardware raid capable device.

---


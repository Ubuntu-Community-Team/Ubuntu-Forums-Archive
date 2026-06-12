---
title: "Dell PowerEdge?"
date: 2012-01-31
forum: Server Platforms
---

### Post by rawmotion on 2012-01-31
Is it possible to put Ubuntu on a Dell Poweredge SC1420
specs:
1 Intel Xeon Processor 3,2 Ghz Hypertrading
4GB ddr2 400 ECC RAM
2 x 160 GB Sata Harddisk
1 Gb Network card onboard
1 Gb Network card extra
video-card.

I've only ever installed it on a spare workstation.
I don't want to get this server machine, and then realize it wont work with Ubuntu...

Thanks

---

### Post by ruffEdgz on 2012-01-31
All the specs that I see on your post look good.

One problem I see when purchasing PowerEdge servers is the RAID controller. Does this SC1420 talk about a RAID controller?

I did a quick search for SC1420 and found this SPEC sheet: [www.dell.com/downloads/global/products/pedge/en/sc1420_specs.pdf](www.dell.com/downloads/global/products/pedge/en/sc1420_specs.pdf)

Is that the machine you want?

If it is, I wouldn't get it since it talked about using a 'SCSI Software RAID 1' which is a Windows only type of RAID controller. If you want a RAID controller that will work with Linux servers, I look for anything with a capital 'H' on it (i.e. PERC H800, PERC H700, etc...). Here is a list of Dell RAID controllers and what they offer: [http://www.dell.com/content/topics/topic.aspx/global/products/pvaul/topics/en/us/raid_controller?c=us&l=en&cs=555](http://www.dell.com/content/topics/topic.aspx/global/products/pvaul/topics/en/us/raid_controller?c=us&l=en&cs=555)

If you want to get a server that is friendly with Linux, I would select the OS to be 'Red Hat'. This will change the page to place parts that will work properly with 'Red Hat'. Once you are done, change the OS back to 'None'.

Hope this helps.

---

### Post by rawmotion on 2012-01-31
Ok thanks.

Is it possible to just not use the RAID? Can I set it up with just separate hard drives?

---

### Post by ruffEdgz on 2012-01-31
> **rawmotion said:**
> Ok thanks.

Is it possible to just not use the RAID? Can I set it up with just separate hard drives?

I don't know the answer personally but I would assume you can't since the PERC Ultra320 (the RAID controller for the server) will be controlling how the operating system will see the drives.

When looking at purchasing a new Dell PowerEdge T110 II from their site just now, I selected the *'PowerEdge T110 II Chassis with Cabled 6x2.5 Hard Drives'* which made me select the H200 PERC card. When I selected *'PowerEdge T110 II Chassis with Cabled 4x3.5 Hard Drives'*, I was able to select an option for **'Onboard SATA, 1-4 Hard Drives connected to onboard SATA Controller -No RAID'** or the software/hardware PERC cards. That first option I placed in bold is probably what you want.

The model you want doesn't look like its available on their site ([http://www.dell.com/us/business/p/poweredge-tower-servers](http://www.dell.com/us/business/p/poweredge-tower-servers)) so its hard to say if you can or can't get the software RAID controller with it. I can only tell you what Dell will offer you with their current lineup.

---

### Post by Dangertux on 2012-01-31
Fair warning if it DOES have the perc6i Ubuntu will hate it. Just a heads up.

---

### Post by rawmotion on 2012-01-31
It's a second hand machine.

I don't know so much about raid.

I thought I could just physically take the raid controller out, and install hard drives normally....

---

### Post by ruffEdgz on 2012-01-31
If the motherboard has on-board SATA ports for you to plug in the hard drives, I don't see why not. It really depends on the motherboard and if it depends on a RAID controller or it also has it on the board.

If you have access to the machine, can open it up and find the SATA ports on the board, then you should be able to use those instead.

Before you take our words for it, I would see if you can find some of this out and then make your decision there. My advise can only be taken if we know the full specs of the machine and I am just doing my best to guess what you are trying to purchase by doing some Google searches.

----

Just in case you don't know what SATA ports look like, here is a link: [http://goo.gl/S8zUY](http://goo.gl/S8zUY)

---


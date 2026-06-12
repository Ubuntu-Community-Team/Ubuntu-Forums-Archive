---
title: "Advice on hardware"
date: 2014-01-21
forum: Server Platforms
---

### Post by AmbiguousOutlier on 2014-01-21
Hello, I want to build a new server and use my current server as a back up device. However I'm not too sure what CPU and how much RAM I should get especially to make it future proof for the next 4 or 5 years. 

It will be a home file sharing server that is permanently on 24/7, so I don't want something that is overpowered and generates a lot of heat and uses up a lot of electricity. I'd rather employ better server management then just get a CPU that can do everything I want to do at the same time. 

Currently I stream locally on the lan high quality mkv's encoded in 1080 and 7.1, and also flac files. I would like the server to be able to handle 3 or 4 streams simultaneously. 

In addition to this I would also like to run blender jobs, but this would likely be overnight, however being able to have one file streaming at the same time would be a requirement. Although here maybe I should learn to read top and use renice properly.

I also constantly mv files around, so home where all my temp/working files are and the os will be on one hdd and I'll also have a 4 or 5 disk raid5 or maybe even a jbod setup. So copying large blender or mkv files currently cause my stream to buffer when watching a file over nfs. 

I would also be running makemkv and ffmpeg whilst streaming. 

Lastly I would like to learn how to implement a LAMP stack, so this would be a future requirement. 


So based on what I use my server for, what CPU and how much RAM should I get plus anything else I may have overlooked. Using my current server I can only do one of these jobs at a time. So multitasking really is the focus for the new one. Plus I'm quite interested in learning what resources these types of programmes actual use, this way I should be able to work out where to spend the money. 

Thanks very much, I know it's a long post, but any advice is much appreciated. 
Rhys

---

### Post by rubylaser on 2014-01-21
If you want to do all of those things well, especially encoding and rendering Blender jobs, you are going to want a quad core processor.  As you probably know, with cycles in Blender you can utilize a GPU if it's available via OpenCL, but if a slower render time doesn't bother you, I wouldn't go with a high end GPU in an always on machine just to reduce initial and log term costs just let the CPU do the rendering.  The streaming media portion of this is easy (even 4 streams) unless you are transcoding 1080p streams, then you'll need a decent CPU. In regards to hardware, more is always going to be better, but as a starting point, I'd be looking at either an AMD FX-8320 or an Intel i5-4570 with 16GB of RAM (2x8GB) if you can swing it.  It's likely you won't be using this computer for all of these same tasks in 4 to 5 years, so the previous CPU's and RAM should be a nice fit.  

If you are willing to pay a little more, some true server hardware like a Supermicro X9SCM-F motherboard with an Intel Xeon E3-1230 v2 would be a very nice setup.  Things you will want to consider are what you will do for RAIDing your hard disks (hardware, ZFS, mdadm, SnapRAID, etc.) and what protocols you will use.

---

### Post by AmbiguousOutlier on 2014-01-22
Thanks for that. 

So is the fundamental difference between Xeon and i5 that the Xeon can support ECC memory. Which I think for my purposes would be beneficial. 

The Xeon-E3's are quite reasonably priced, I am tempted to go down that route. I would like to put 4x4Tb drives on a raid and ideally SATAIII. But most mobo's including the one you mention are are SATAII with a couple III's. Unless I'm missing something, it looks like there aren't any chipsets that include 6 SATAIII ports. Or should I really be buying a separate [SAS Raid controller](http://www.amazon.co.uk/HighPoint-RocketRAID-2710-PCI-Express-Controller/dp/B003YKWAH4/ref=sr_1_2?ie=UTF8&qid=1390398034&sr=8-2&keywords=sas+raid+controller)?

Next thing I would like clarification on is memory, do I get two sticks of; 
Slower [Registered](http://www.ebuyer.com/183983-hp-8gb-ddr3-1333mhz-registered-ecc-memory-module-cl9-500662-b21) @ £137
Faster [Unbuffered ECC](http://www.ebuyer.com/393263-kingston-8gb-1600mhz-ecc-module-kth-pl316e-8g) @ £89

This build might be more expensive than I first thought, at least I've got until the 17th April before I can buy it.

---

### Post by rubylaser on 2014-01-22
In regards to the processors, Xeons support ECC, this Xeon is hyper-threaded vs. the i5-4570 that isn't, both support VT-D for PCI Passthrough if you ever want to use this as a hypervisor host.  You need unbuffered ECC with that supermicro board. If you are going with spinning disks, you won't see any difference in the speeds attached to a SATAII head vs. SATA III. If you are using SSD's, I would suggest you pickup something like the [IBM M1015 off Ebay]("http://www.ebay.co.uk/itm/IBM-ServeRaid-M1015-SAS-SATA-PCI-e-RAID-Controller-46M0861-/281250381699?pt=UK_Computing_ComputerComponents_InterfaceCards&hash=item417bd43f83") and [flash it to IT mode]("http://www.servethehome.com/ibm-serveraid-m1015-part-4/"). If you have the money, the Xeon platform would be very nice.  That motherboard also support IPMI which is an awesome way to administer your server.

---

### Post by AmbiguousOutlier on 2014-01-23
> **rubylaser said:**
> you won't see any difference in the speeds attached to a SATAII head vs. SATA III.

What's the bottle neck then? Would I not get these speeds when transferring files internally? 


I think I will go by your recommendations. Although I hold off getting the raid set up and just continue to use my server as a file server for now. 

Thanks for your guidance.

---

### Post by rubylaser on 2014-01-23
> **RhysGM said:**
> What's the bottle neck then? Would I not get these speeds when transferring files internally? 
SATAII supports 300MB/s and SATAIII supports 600MB/s.  There isn't a spinning consumer disk that can do 300MB/s, so you won't saturate that connection.  If you were going with modern SSDs, to get maximum throughput you would need SATAIII heads.  For most fileservers, the bottleneck comes from the type of RAID setup, the type of transfer (sequential vs. random io), the number of users accessing the system, the file share protocol used, and then the gigabit connection that maxes out at 125MB/s.  

This will be a great build. Please post back with your results:)

---

### Post by AmbiguousOutlier on 2014-01-23
One of your comments got me googling. I would quite like to use this run virtual machines, but am I understanding this correctly. This machine as a headless server can host multiple virtual machines, that can be virtualised on a low powered laptop effectively turning it into a superfast multicore machine. 

Can I effectively set up multiple virtual machines and allocate a certain number of logical cores and ram to each? Then run certain processes on each VM and log in and out but still keeping the VM running in the background on the server?

If I can that sounds like a fun new project. I can imagine more RAM might be useful if I want to do that?

---

### Post by rubylaser on 2014-01-23
Yes, this machine is ideal for home virtualization.  You can choose your hypervisor of choice like Proxmox, Citrix Xenserver, ESXi, or just use KVM directly and run VMs on this box. The benefit of VT-D which this hardware supports is that you can pass hardware through to the VM's directly.  More RAM could be benefical if you planned on alot of VMs.  This board maxes out at 32GB of RAM.

---

### Post by AmbiguousOutlier on 2014-01-24
Can you see anything wrong with this [RAM](http://www.amazon.co.uk/Kingston-ValueRAM-240-pin-PC3-12800-unbuffered/dp/B00DB3ZTR2/ref=sr_1_3?s=computers&ie=UTF8&qid=1390563504&sr=1-3&keywords=unbuffered+ecc+ddr3+1600+8gb+-non) It seems a little cheap for £55/$91 32GB of ECC.

---

### Post by rubylaser on 2014-01-24
No, but that listing has to be wrong.  32GB of Kingston unbuffered ECC should be over [COLOR=#000000]£250[/COLOR]. Here's a [link to standard pricing for (1) 8GB stick.]("http://www.amazon.co.uk/Kingston-KVR1333D3E9S-8G-240-Pin-DDR3-RAM/dp/B0064Z71NY/ref=sr_1_fkmr1_2?s=computers&ie=UTF8&qid=1390574545&sr=1-2-fkmr1&keywords=KVR1333D3E9S+32gb") If you can get it for that price, I'd buy it quick :)

---

### Post by AmbiguousOutlier on 2014-01-24
Bought and hopefully the correct RAM will be sent. I looked at the manufacture reference code on the listing and did an amazon search on that [£308](http://www.amazon.co.uk/s/ref=nb_sb_noss?url=search-alias%3Dcomputers&field-keywords=KVR16E11K4%2F32) was the next cheapest! Bargain of the year I think.

---

### Post by rubylaser on 2014-01-24
I hope it works out for you :) Please keep us posted.

---

### Post by AmbiguousOutlier on 2014-01-27
They realised their mistake and cancelled my order :(

Here's my current shopping list, any comments before I click "buy now";

[Xeon E3 1230v2](http://www.amazon.co.uk/gp/product/B0084JTFMI) £172
[Supermicro MBD-X9SCM-F-O](http://www.amazon.co.uk/gp/product/B004WKRDA4) £143
[16GB(2x8GB) ECC RAM](http://www.amazon.co.uk/gp/product/B00ARI1FVI) £172
[WD RE Mission Critical Enterprise 1TB](http://www.amazon.co.uk/gp/product/B00D38U4GQ) £79
[Fractal Design Define R4 PC Case](http://www.amazon.co.uk/gp/product/B008NFWGXI) £83
[Corsair AX 760 PSU](http://www.amazon.co.uk/gp/product/B00A74X9SO) £123

In total £773. 

I'll add the 6+ disk RAID setup later and I might add another 16GB of Ram later too.

---

### Post by rubylaser on 2014-01-27
I figured that was too good to be true unfortunately :) In regards to your build, everything looks good other than I have a concern about the RAM.  Supermicro boards can be finicky with the RAM, and that Amazon link has absolutely no mention of the model number. The [one I linked to earlier]("http://www.amazon.co.uk/Kingston-KVR1333D3E9S-8G-240-Pin-DDR3-RAM/dp/B0064Z71NY/ref=sr_1_fkmr1_2?s=computers&ie=UTF8&qid=1390574545&sr=1-2-fkmr1&keywords=KVR1333D3E9S+32gb") I know works and it's cheaper.  Other than that, this should be a very nice machine when you are done.

---


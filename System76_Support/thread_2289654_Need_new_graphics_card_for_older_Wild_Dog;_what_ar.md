---
title: "Need new graphics card for older Wild Dog; what are my options?"
date: 2015-08-05
forum: System76 Support
---

### Post by watchpocket on 2015-08-05
I have a System76 [Wild Dog Performance desktop unit]("https://system76.com/desktops/wild-dog") that I got in early 2010 (model number wilp6).  Its graphics card is an [Nvidia Geforce GTS 250]("http://www.amazon.com/exec/obidos/ASIN/B005640FSW/ref=pe_301860_26203570_tex_id") (1GB, 256-Bit, GDDR3, PCIe 2.0), made by Gigabyte (an enlargable picture of it is [here]("http://www.clubic.com/actualite-271134-geforce-gts-250-test-clubic.html")).   Recently I got a 2560x1600-resolution [30-inch Nixeus monitor]("http://www.amazon.com/Nixeus-Vue-2560x1600-WQXGA-Monitor/dp/B00CHDHE0W/ref=sr_1_3?s=electronics&ie=UTF8&qid=1438814148&sr=1-3&keywords=nixeus+vue") which I'm very happy with and which is connected via the card's DVI port. 

**My problem is that I want to get another of this same monitor, but a dual-link DVI connection is necessary for the monitor to run at the 2560x1600 resolution, and the card has only one DVI port.**

So I need to replace the card with one that has two DVI ports, is eight-and-a-quarter inches long (or shorter), and will otherwise be compatible with my system.  I've been looking at [this PNY GTS 450 card]("http://www.amazon.com/PNY-GeForce-PCI-Express-Graphics-VCGGTS4501XPB/dp/B0041HN6P4/ref=sr_1_6?s=electronics&ie=UTF8&qid=1438812993&sr=1-6&keywords=geforce+gts+450"), which does have the two DVI ports, and appears to be the right length. *("Product Dimensions: **          8.2 x 4.2 x 1.5 inches**; 2.5 pounds")*.

But I don't know enough about the potential unexpected *gotchas* of swapping graphics cards to really know *what* I should, or could, get.  I'm not a gamer, but I do want the higher resolution in both monitors. My power supply is 500 watts.

The [250's specs can be seen here]("http://www.geforce.com/hardware/desktop-gpus/geforce-gts250/specifications") and the [450's specs here]("http://www.geforce.com/hardware/desktop-gpus/geforce-gts-450/specifications").  I started comparing them, but I'm not sure which of the differences between the cards are relevant. (I'm also concerned about any possible conflicts with drivers.) 

I'm hoping someone from System76 -- or anyone else -- can weigh in as to whether the 450 would be an appropriate, workable replacement, or can suggest a card that would be. 

 Thanks very much.

 Here's a bit more info:```
--> [COLOR=#0000ff]sudo lshw -C display[/COLOR] 
  *-display               
       description: VGA compatible controller
       product: G92 [GeForce GTS 250]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:43 memory:e2000000-e2ffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:e000(size=128) memory:e3000000-e301ffff
```

---


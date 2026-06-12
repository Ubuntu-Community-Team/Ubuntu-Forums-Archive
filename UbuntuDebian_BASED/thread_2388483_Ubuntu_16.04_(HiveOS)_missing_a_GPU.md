---
title: "Ubuntu 16.04 (HiveOS) missing a GPU"
date: 2018-04-03
forum: Ubuntu/Debian BASED
---

### Post by pljenkins522 on 2018-04-03
Hi guys! So I am running a 6 GPU mining rig. It's been going along smashingly on Windows 10 for about 8 months with no problems bringing up the 6 GPUs and running stable for days at a time, so I know this isn't a hardware problem at least in terms of defective interface equipment. Since Windows has decided it's going to arbitrarily phone home and update itself regardless of my settings, I'm moving on to a real OS for mining.


I've done what I can with the BIOS (the motherboard is a Biostar TB85 6+ mining board with 1xPCIe 16 slot and 5xPCIe 1 slots) including enabling above 4G encoding and setting all slots to Gen1 (which seems like it's superfluous as the cards are all on 1x to 16x risers, and BIOS correctly shows Gen1 detected on the 16x slot), and internal graphics are disabled. I am displaying through the card plugged into the 16X slot. Anyway, config has 3 GTX1060 3Gb cards on slots 1,2(the 16x slot),and 3 and RX 4XX cards on slots 4,5,and 6. The card in slot 1 is consistently missing. When I go to look at the lspci output I get this.([https://i.imgur.com/4kTPbnz.jpg](https://i.imgur.com/4kTPbnz.jpg))


As you can see, there are 6 PCIe root ports allocated to PCI bridge. So it looks like from a hardware standpoint all 6 slots are accounted for. However, when you go to the dgmesg output I see that there is no bridge window allocated to 1c.0 bus 2 bridge([https://i.imgur.com/OdCPVNI.jpg](https://i.imgur.com/OdCPVNI.jpg)), that shows up here([https://i.imgur.com/9mTKTQJ.jpg](https://i.imgur.com/9mTKTQJ.jpg)) in the bridge window listing. Now, curious, I have 6 PCIe slots, but there are 7 showing here. I have the internal GPU disabled in BIOS, so I don't think that would show up here, so what is that 7th device? 


Anyway, I'm at a loss as to why it's failing to allocate a bridge window for this, but I'm assuming this is why GPU6 is MIA. Could someone help me get a grip on how these bridge windows work and how I might convince Ubuntu to assign a window for this slot? I'm at a loss here. Thanks!

---

### Post by deadflowr on 2018-04-03
*Thread moved to **Ubuntu/Debian BASED***

---


---
title: "Home server hardware choices"
date: 2011-05-17
forum: Server Platforms
---

### Post by bavman on 2011-05-17
Im wanting to build a home file server but im having a bit of trouble picking out specific hardware. This is what ive considered so far:

mobo/cpu/vga combo: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813128452](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128452)   ----- for 13w tdp
ram: 1 or 2gb 
harddrives: 4-5 In raid 5 or 10, havent decided yet

I was wondering if I would need a raid card or if software raid through ubuntu would be enough, and would the cpu be able to handle it fine? What experience do you guys have with builds like this? Recommendations are appreciated. Thanks

---

### Post by dtfinch on 2011-05-18
It seems ok. You're limited to 4 sata drives unless you get an addin card, or you make the 5th an IDE drive, but the largest I've seen is 500gb, and it might be slower than the others. With software raid you'll want a raid 1 to put the OS on (so 1 tiny [maybe 8-20gb] partition on each drive dedicated to the OS), since you can't boot directly off software raid other than raid 1. Another option is to put the OS on another disk, or an ssd.

The linked motherboard has a regular slow PCI slot, not a PCIe slot, so I'd avoid an addin raid or sata card.

I'm more comfortable with raid 10 than with raid 5, though I haven't had problems with either. With 4 or more drives, raid 6 is also an option, being able to survive the loss of any 2 disks, but it has the slowest write speeds.

I'd try to leave a little space at the end of each drive. If you don't, and the raid partitions go to the very end of the disk, with the default 0.90 metadata, mdadm sometimes gets confused while assembling the raid and uses the full disks instead of the partitions, damaging the raid. It'll also avoid problems if you replace a drive, and the new disk turns out to be a few mb smaller, though rare.

---

### Post by bavman on 2011-05-18
How about using a sata port multiplier? Is that a good idea or not? The server wont really have that much trouble so if it decreases read/write speeds a bit its no big deal. If its a decent option could you suggest one?

Thanks again for the help.

---

### Post by dtfinch on 2011-05-18
I hadn't thought of port multipliers, but it looks like the Intel NM10 chipset on that motherboard doesn't support them, judging by [http://www.intel.com/Assets/PDF/datasheet/322896.pdf](http://www.intel.com/Assets/PDF/datasheet/322896.pdf) and [https://ata.wiki.kernel.org/index.php/SATA_hardware_features](https://ata.wiki.kernel.org/index.php/SATA_hardware_features)

---


---
title: "DIY ESATA enclosures?"
date: 2008-01-26
forum: The Cafe
---

### Post by jondecker76 on 2008-01-26
I'm just about finished making a nice rack-mount computer (its going to be used for LinuxMCE, which is Kubuntu based).

I wanted my computer in a 4U rackmount (which is pretty much done now), and all of my drives in an external enclosure connected with ESATA.

I've never messed with ESATA (hell, I've never had a SATA drive before)..  While shopping around, I've noticed that a rackmount enclosure for hot swappable SATA drives cost A LOT of money (the cheapest ones I was seeing were around $700!) I would like to house anywhere from 6-10 SATA drives in a rackmount unit (I would like it to look nice as well). Does anyone know where I would start to make my own to save some money? Any DIY links or useful information I should know before stariing? Can someone recomend a PCIe ESATA card that works well in linux, and has at least 6 ports?

thanks

Jon

---

### Post by mips on 2008-01-26
Might be hard but here is an idea, [http://www.usb-ware.com/sata-rack-mount-5-drive-rm5s2p.htm](http://www.usb-ware.com/sata-rack-mount-5-drive-rm5s2p.htm)


You dont really need a 6port sata card as you can use a sata port multiplier(sataII only i think), example:
[http://himself.wordpress.com/2006/07/12/laptop-with-one-sata-port-add-one-sata-port-multiplier-host-is-to-ifs-as-device-is-to-ncq-sata-approaches-sas-power/](http://himself.wordpress.com/2006/07/12/laptop-with-one-sata-port-add-one-sata-port-multiplier-host-is-to-ifs-as-device-is-to-ncq-sata-approaches-sas-power/)

[http://www.hardforum.com/showthread.php?p=1031973661](http://www.hardforum.com/showthread.php?p=1031973661)

---

### Post by jondecker76 on 2008-01-26
Great information!  Thanks a ton!

---

### Post by mips on 2008-04-15
How is your project coming along?

---

### Post by jondecker76 on 2008-04-17
The project is going great - i built a LinuxMCE system with a rackmount case I bought off of ebay. It has 6 internal drive bays, so I didn't need to build an ESata enclosure. Right now I have a 500GB system disk, and 5x 1TB drives in Raid 5. Still, when I expand eventually, I will need an ESata enclosure.

---


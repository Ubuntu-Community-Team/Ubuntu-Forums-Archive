---
title: "UltraSparc 60"
date: 2007-04-20
forum: Sun Sparc Users
---

### Post by dannytherocker on 2007-04-20
Hi,
a friend of mine will be giving to me a Sun UltraSparc 60 running @ 300 mhZ with 640 mb ram...
my answer is:
Since I would use it as a ftp server/data storage/etc etc...how many Gbs (Hd, I mean) does the motherboard recognize ?? someone told me less or more 20 gbs...which wouldn't be enough for a server...
Thanks

---

### Post by netztier on 2007-04-20
> **dannytherocker said:**
> Hi,
a friend of mine will be giving to me a Sun UltraSparc 60 running @ 300 mhZ with 640 mb ram...
my answer is:
Since I would use it as a ftp server/data storage/etc etc...how many Gbs (Hd, I mean) does the motherboard recognize ?? someone told me less or more 20 gbs...which wouldn't be enough for a server...
Thanks

Well.. If you want to spend the money on SCSI Disks with 80pin SCA connectors: go ahead. Thet's the only disks you'll be able to fit into an U60's hard drive slots - provided you have a Sun-specific cradle to hold them.
I think it should accept any disk size the onboard SCSI controller accepts - 72 or 144 Gig might work; see [http://sunsolve.sun.com/handbook_pub/Systems/U60/U60.htmln](http://sunsolve.sun.com/handbook_pub/Systems/U60/U60.htmln)

IDE or SATA disks won't work in a Sun, unless you find a PCI controller to connect them to and use some form of adapter to put them into the 5.25" slots - provided the controller is supported by the SPARC linux kernel.

Alternative: find a supported USB2 chipset and use external USB2 drives. The U60's onboard ethernet is 100Mit/s only, so USB drives might be fast enough.

best regards

Marc

---

### Post by dannytherocker on 2007-04-20
> **netztier said:**
> Alternative: find a supported USB2 chipset and use external USB2 drives. The U60's onboard ethernet is 100Mit/s only, so USB drives might be fast enough.

Thanks a lot for your answer...so you say I can use one (or more) scsi hds up to 72/144 gbs.....Good news, but do you know supported USB2 pci (I think, pci) controllers for UltraSparc ???

---

### Post by netztier on 2007-04-20
> **dannytherocker said:**
> Thanks a lot for your answer...so you say I can use one (or more) scsi hds up to 72/144 gbs.....Good news, but do you know supported USB2 pci (I think, pci) controllers for UltraSparc ???

PCI is the only option you'll have. I don't know which Chipsets are actually supported, you'll have to google-search for it a bit. I think I've seen text snippets about using PCI USB cards in SPARC systems on the web ("PCI USB Sparc Linux" might be helpful search terms...)

As long as the card uses a mainstream USB chipset, there shouldn't be problems, so don't buy overly cheap and exotic. After all, newer Suns (such as Sun Blades) have USB ports also.

best regards

Marc

---

### Post by nfld.republic on 2007-04-20
The Sun Ultra60 can only accomodate two (2) internal SCA80 disk slots; other than using an adaptor to put another disks or two in the 5.24" trays you can't get many disks into the box.  It does has an external SCSI2 connector.  You can pick up a cheap external enclosure on eBay and fill it with disks.  While SunSolve likely lists 72 or 144 GB disks, I suspect that you'll be able to use 300 GB disks.

You cand dig a little deeper and see if you can find an external disk enclosure that allows you to use IDE or SATA disks in the enclosure but use the SCSI connector to attach to the Ultra60.  I have a couple of these at work, but they ain't cheap....

HTH
Mike

---

### Post by dannytherocker on 2007-04-21
Thanks to all of you !

---


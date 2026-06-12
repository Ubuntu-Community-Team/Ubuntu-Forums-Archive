---
title: "Cheap Hardware raid for Ubuntu Server?"
date: 2011-10-17
forum: Server Platforms
---

### Post by r00lz on 2011-10-17
Hello everyone,
I wanna build ubuntu server system with hardware raid 1 (not mdadm). Whats suggestions (brands, models?) of cheap raid 1 controllers ?

---

### Post by FiVAL on 2011-10-17
I would go with btrfs... It's the default in the new Fedora version... (but it is still software based, i know)

---

### Post by r00lz on 2011-10-17
Any more suggestions? BTW SATA2 interface.

---

### Post by samosamo on 2011-10-17
Whenever I think of "cheap hardware RAID" I think of all of those used Dell PERC5/i on eBay. They are pulls from working systems. It is a rebranded LSI Megaraid 8408, and it doesn't get any cheaper.

They could be $100-150 buy-it-now but I see them go as low as $50, without battery. You will need to replace the battery anyway because they are getting old enough now where the original OEM batteries are near their end of life. I see aftermarket batteries go for $15/ea.

---

### Post by rubylaser on 2011-10-17
> **FiVAL said:**
> I would go with btrfs... It's the default in the new Fedora version... (but it is still software based, i know)

This isn't the case with the current Fedora 15 and won't be the case with Fedora 16.  It was originally supposed to be included, but it will no longer be the default filesystem even in [Fedora 16]("http://lwn.net/Articles/454347/").  The lack of a good fsck is the main problem to the adoption of Btrfs at this point.

---

### Post by rubylaser on 2011-10-17
The PERC 5/i is a nice card (minus needing to do the pin mod on some motherboards), but for a simple RAID1, the  [IBM ServeRaid BR10i]("http://www.ebay.com/itm/IBM-ServeRaid-BR10i-SAS3082E-R-RAID-Controller-44E8690-/120786452564?pt=LH_DefaultDomain_0&hash=item1c1f6f0054#ht_1446wt_907") is fine.  Also, in the future, if you decide against hardware RAID it's very easy to flash with IT firmware and can be used in Windows, Linux, FreeBSD, and Solaris as a simple HBA.

This is a nice writeup about these [cards]("http://www.servethehome.com/ibm-serveraid-br10i-lsi-sas3082e-r-pciexpress-sas-raid-controller/").

---

### Post by r00lz on 2011-10-17
Hmm how about that [http://www.ebay.co.uk/itm/3WARE-9500S-4LP-4-PORT-SATA-RAID-CARD-w-128MB-Mem-CABLE-/320685583041?pt=COMP_EN_Networking_Components&hash=item4aaa59aac1](http://www.ebay.co.uk/itm/3WARE-9500S-4LP-4-PORT-SATA-RAID-CARD-w-128MB-Mem-CABLE-/320685583041?pt=COMP_EN_Networking_Components&hash=item4aaa59aac1) this is old PCI, but only for small system needed. And what battery do and is it necessary?

---

### Post by rubylaser on 2011-10-17
Personally, I wouldn't bother with an old PCI card, that wouldn't allow for future re-use. If you have an open PCIe x8 or x16 slot, either the PERC or the IBM card I mentioned are both much better cards, and only $10 - $30 more expensive.  The battery is to enable the write cache (makes your writes to the disks MUCH faster).

---

### Post by r00lz on 2011-10-17
Ok... how about that [http://www.ebay.co.uk/itm/DELL-PERC-5-IR-SAS-SATA-PCI-E-XP-VISTA-WIN7-INTERNAL-CONTROLLER-CARD-W-BRACKET-/220875946086?pt=LH_DefaultDomain_0&hash=item336d3b7866](http://www.ebay.co.uk/itm/DELL-PERC-5-IR-SAS-SATA-PCI-E-XP-VISTA-WIN7-INTERNAL-CONTROLLER-CARD-W-BRACKET-/220875946086?pt=LH_DefaultDomain_0&hash=item336d3b7866) ? is ubuntu installer see this controller without additional drivers or need something special (except pin mod) ?

---

### Post by FiVAL on 2011-10-17
> **rubylaser said:**
> This isn't the case with the current Fedora 15 and won't be the case with Fedora 16.  It was originally supposed to be included, but it will no longer be the default filesystem even in [Fedora 16]("http://lwn.net/Articles/454347/").  The lack of a good fsck is the main problem to the adoption of Btrfs at this point.

Thx 4 the update... I didn't know that btrfs didn't make it in Fedora 16 :-( Although I use it for half a year with Ubuntu and I like it very much... I hope the btrfs-tools get mature very soon.

---

### Post by samosamo on 2011-10-17
> **r00lz said:**
> Ok... how about that [http://www.ebay.co.uk/itm/DELL-PERC-5-IR-SAS-SATA-PCI-E-XP-VISTA-WIN7-INTERNAL-CONTROLLER-CARD-W-BRACKET-/220875946086?pt=LH_DefaultDomain_0&hash=item336d3b7866](http://www.ebay.co.uk/itm/DELL-PERC-5-IR-SAS-SATA-PCI-E-XP-VISTA-WIN7-INTERNAL-CONTROLLER-CARD-W-BRACKET-/220875946086?pt=LH_DefaultDomain_0&hash=item336d3b7866) ? is ubuntu installer see this controller without additional drivers or need something special (except pin mod) ?

I wouldn't trust an eBay auction written in Comic Sans.

edit: Actually, I wouldn't trust anything written in Comic Sans.

---

### Post by r00lz on 2011-10-17
For me it looks trusted. My priority to know is this card compatible with Ubuntu/Debian by default?

---

### Post by rubylaser on 2011-10-17
You should be fine with that, but you'll really want to get the Perc 5/i or 6/i.  Or, just go with the IBM card I posted earlier...
[http://www.ebay.co.uk/itm/IBM-44E8689-IBM-ServeRAID-BR10i-Storage-controller-RAID-SATA-300-SAS-low-/170698650332?pt=LH_DefaultDomain_0&hash=item27be6eb2dc]("http://www.ebay.co.uk/itm/IBM-44E8689-IBM-ServeRAID-BR10i-Storage-controller-RAID-SATA-300-SAS-low-/170698650332?pt=LH_DefaultDomain_0&hash=item27be6eb2dc"). This will work fine in Ubuntu without needed to install any drivers.

---


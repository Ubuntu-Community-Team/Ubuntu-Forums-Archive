---
title: "Ubuntu 10.04 server to 14.04"
date: 2015-01-12
forum: Server Platforms
---

### Post by dfrandin on 2015-01-12
I currently have a Dell PowerEdge 750 running my home server on Ubuntu 10.04 server. I realize 10.04 is going EOL in just a few months, so I want to get it upgraded to 14.04. My experience with doing "do-release-upgrade" in the past between LTS has been abysmal, so I want to do a clean install to two new larger drives. The system currently runs two 250GB SATA drives in RAID1 on a Dell/Adaptec AAC-RAID (thats what lspci shows, I forget the Dell model #, but it came with the Dell server and takes up one of the PCI-x slots). My question is this, once I install a clean copy of 14.04 server, I'd like to take one of original mirror set, slave it via a USB-SATA adapter, and copy over the 150+GB of movies/media/stuff from the old install.. I'm not familiar with whether a RAID1 drive from a mirror set from this type of controller can be read successfully by a non-native SATA port... I've already done a "dpkg -get-selections" and "dselect-get-selections" both to files on an other machine... Is this doable??

Thanks
Dave

---

### Post by MAFoElffen on 2015-01-12
I have some Dell servers... If a card that came with it when it was ordered, you can find out exactly what it is (and what came in it in the box) from the Asset Tag number and using that number on their support site. On their cards, even though the Chipset it will show in the BIOS Post messages as HBAx, with a message saying something like CERC4...", model subtype and BIOS firmware version number, etc, before it probes and inits the drives. Some of the later cards were PERC5, PERC6...

Some of the lower end cards, ones that usually only offered RAID 0, 1 or JBOD... If 1 or JBOD > can go an a SATA. Other higher, costlier cards, usually when they 0, 1, 10, 5, 50, 6, 60... You have to define a JBOD as a logical RAID1 of 1. Drives used on them as RAID1, still work on SATA. If you hit the hot-key to drop into the card's BIOS, it will also tell you which card it is and the firmware revision. But the thing to do, would be to test that first.

Even on the lower end cards, their early CERC was 6 channel, so I don't know for sure what you may have. So it might be possible to hang other drives off your card to copy things over, without going to the mainboard SATA ports. I think I remember that having 1 native IDE and 2 native SATA ports on the mainboard. 

If not possible, you could connect through a USB adapter (would be way slow), but it would be a faster transfer to put in another box, use a crossover cable and copy through an adhoc network directly between those two boxes. (point to point). Still faster if to SATA.

Note: Linux kernel ID's them from the underlying chipset, not specifically from the aftermarket branding.

---

### Post by dfrandin on 2015-01-13
According to dmidecode, its a  CERC-SATA-6CH.. I guess my main question is.. can I read *one* of the mirror set independantly via a USB-SATA adapter, or you mentioned, using one of the currently disabled onboard SATA ports.. Bottom line, is I'm going to do a clean install of 14.04 as there's a lot of cruft on the current install of 10.04 plus I'll be replacing the 250GB drives with 1TB..

Idea: Would it be safe to down the server, pull one of the mirror set, and *try* reading it via a USB-SATA adapter? I certainly don't ever intend on writing to the disk this way, I simply want to get a lot of the data off it..

---


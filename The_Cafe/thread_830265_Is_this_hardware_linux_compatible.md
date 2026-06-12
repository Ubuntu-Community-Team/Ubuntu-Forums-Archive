---
title: "Is this hardware linux compatible?"
date: 2008-06-15
forum: The Cafe
---

### Post by Stefanie on 2008-06-15
i have to buy a new desktop pc for my family, and i want to install ubuntu on it. i found a computer in a local store with these specs:
# Samsung SH-S203D DVD±RW S-ATA 20x bulk black
# Intel Pentium Dual Core E2160 1.8GHz LGA775 1Mb FSB800 Boxed
# Apacer Embedded Card Reader 16-in-1 USB2.0 Black
# WD Caviar SE 1600AAJS 160GB S-ATA II 8Mb
# Logitech OEM Internet 350 Keyboard Azerty BE Black
# Logitech OEM RX250 Optical Mouse Black
# MSI 945GCM5-F V2 S775 i945GC VGA PCIe DDR2 µATX
# 2x Transcend JetRam DDR2 1024MB PC5300 
# MSI nVidia GeForce NX8400GS-TD256E PCIe 256Mb TV Out & DVI

will ubuntu work on this computer? i mean "work out of the box", my family members are computer illiterate so i want to keep it as simple as possible. i don't mind installing a proprietary driver but i don't want to have too much hassle with it. 

the sound card and network card don't seem to be listed? any advice on what (not) to buy? (i want both wired and wireless connectivity. )

---

### Post by xfceuser on 2008-06-15
why dont you test install ubuntu.
its the safest way.
also running the LiveCD can give you an idea.

---

### Post by John.Michael.Kane on 2008-06-15
All should work without issue. Only item that may be questionable is the card reader.

Also the MSI 945GCM5-F V2 has a Realtek RTL8111B chip, which is the same chip on the board I am running, and Ubuntu version 7.04-8.04 recognized it with out issue, however. YMMV.

---

### Post by Stefanie on 2008-06-16
ok thanks. i can't test install ubuntu because they build the computers on demand. you can change the specs if you want to.

---

### Post by mips on 2008-06-16
> **John.Michael.Kane said:**
>  Only item that may be questionable is the card reader.


+1

The only way to know if it will work is to find out what chipset that cardreader uses and then check linux compatibility.

EDIT: I did a google search and that card reader seems to have support in Linux Kernel 2.4 and above so you should be ok.

---

### Post by Stefanie on 2008-06-16
ok thanks! i think i'm going for an intel PRO/100 M PCI network card. any ideas on what brands to buy for wireless?

---

### Post by LaRoza on 2008-06-16
> **Stefanie said:**
> ok thanks! i think i'm going for an intel PRO/100 M PCI network card. any ideas on what brands to buy for wireless?

Intel for wireless for full compatibility.

(Intel Video and Wireless works out the of box with Linux)

---

### Post by Stefanie on 2008-06-16
the shop doesn't seem to have intel wireless network cards... 
does anyone knows if one of these cards work on hardy?
# Netgear WG311T 108 Mbps Wireless PCI Adapter
# Linksys WMP54G Wireless-G PCI Adapter 
# SMC WPCIT-G 108Mbps Wireless PCI Adapter 
# Netgear WG311 54 Mbps Wireless PCI Adapter 

I checked the ubuntu community docs [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) but the information isn't always up-to-date so I'd like to hear your comments.

---

### Post by John.Michael.Kane on 2008-06-16
> **Stefanie said:**
> the shop doesn't seem to have intel wireless network cards... 
does anyone knows if one of these cards work on hardy?
# Netgear WG311T 108 Mbps Wireless PCI Adapter
# Linksys WMP54G Wireless-G PCI Adapter 
# SMC WPCIT-G 108Mbps Wireless PCI Adapter 
# Netgear WG311 54 Mbps Wireless PCI Adapter 

I checked the ubuntu community docs [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) but the information isn't always up-to-date so I'd like to hear your comments.

According to the wiki.

Linksys WMP54G Wireless-G PCI Adapter (Ver 4.0) works out of the box
(Ver 4.1, and 4.5 of the card above has issues) so unless you can get a V.4 of the card you may have issues.
	
Netgear WG311T 108 Mbps Wireless PCI  worked out of the box Ubuntu 6.06 6.10, and 7.04 hardy is unknown-untested.

SMC WPCIT-G 108Mbps Wireless PCI Adapter This adapter does not seem to have had any testing done.

Netgear WG311 54 Mbps Wireless PCI Adapter (v3) Worked under (Hardy), however. It will require the install of ndiswrapper and the driver.

Unless the version numbers are known or can be told to you, it is going to be hard to pick one, having said this you might have luck with the WG311T or WG311.

---

### Post by Stefanie on 2008-06-17
> **John.Michael.Kane said:**
> According to the wiki.

Linksys WMP54G Wireless-G PCI Adapter (Ver 4.0) works out of the box
(Ver 4.1, and 4.5 of the card above has issues) so unless you can get a V.4 of the card you may have issues.
	
Netgear WG311T 108 Mbps Wireless PCI  worked out of the box Ubuntu 6.06 6.10, and 7.04 hardy is unknown-untested.

SMC WPCIT-G 108Mbps Wireless PCI Adapter This adapter does not seem to have had any testing done.

Netgear WG311 54 Mbps Wireless PCI Adapter (v3) Worked under (Hardy), however. It will require the install of ndiswrapper and the driver.

Unless the version numbers are known or can be told to you, it is going to be hard to pick one, having said this you might have luck with the WG311T or WG311.

thanks. I have no idea about the version numbers so it seems that the netgear WG311T is the safest bet. 
on my current notebook i installed ubuntu without checking the drivers, apparently i was very lucky that everything worked out of the box! i didn't know it would be difficult to find good cards except for intel...

---


---
title: "Managinithout gng studio without gnome"
date: 2013-07-18
forum: Ubuntu Studio
---

### Post by mashaffer on 2013-07-18
While searching to find out how to get wireless working on my new studio intallation (macbookpro4,1) I find that all of the help seems to assume a gnome environment. For example go to system=>hardware drivers and install broadcom drivers. There is no such location in xfe as far as I can tell. I tried to figure out how to start a gnome session temporarily but have failed. How do you handle this?

mike

Sorry about the munged up topic. My curse keeps jumping around while I type.

---

### Post by ajgreeny on 2013-07-18
Command **jockey-gtk** should start the **Additional Drivers**  utility (note the name; not Hardware Drivers), if you can't find it in the menu, though it is in Xubuntu 12.04 menu under Settings.

---

### Post by mashaffer on 2013-07-19
Thank you. Installed jockey-gtk but got no such command but I also installed jockey-kde and it ran. Activating Broadcom failed though...

2013-07-19 16:40:07,796 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-07-19 16:40:07,874 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-07-19 16:40:08,008 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-07-19 16:40:15,264 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-07-19 16:40:19,034 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-07-19 16:40:29,709 WARNING: modinfo for module wl failed: ERROR: Module wl not found.

2013-07-19 16:40:29,777 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-07-19 16:40:39,260 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-07-19 16:40:39,391 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-07-19 16:40:39,460 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted

Looks like I need to do something about wl. modprobe finds no such module.

mike

---

### Post by mashaffer on 2013-07-19
BTW: data on my airport card...

 *-network UNCLAIMED     
       description: Network controller
       product: BCM4321 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:97300000-97303fff

mike

---

### Post by jejeman on 2013-07-20
See if this helps
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
[https://help.ubuntu.com/community/BroadcomSTA%28Wireless%29](https://help.ubuntu.com/community/BroadcomSTA%28Wireless%29)

---

### Post by mashaffer on 2013-07-20
Part of my problem is that I don't really understand modules and modprobe  nor blacklists. Also as near as I can tell modules are handled differently in the latest versions of Ubuntu than in earlier as a lot of what I read seem to references directories used by modprobe that don't exist on my system. I probably need an up to date tutorial on the subject.

mike

---

### Post by jejeman on 2013-07-20
Well, it is better that moderators move this thread to one more convenient place for solving network problems with Broadcom wifi cards.
This "problem" is not specially Ubuntu Studio related, and you will get more help there.

---


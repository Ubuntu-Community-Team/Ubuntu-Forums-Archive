---
title: "MAAS Intel SFP PXE boot"
date: 2018-03-19
forum: Server Platforms
---

### Post by acneteng on 2018-03-19
I have an issue where I am PXE booting a Dell R720xd with 10GB SFPs using MAAS 2.2.  I am using 16.04 LTS as the potential image.  When I boot the SFP is not recognized and the boot process stalls.  I found a new driver from Intel and I also saw a post about configuring the driver based on the following statement [COLOR=#333333][FONT=&amp]"allow_unsupported_sfp=1".  [/FONT][/COLOR]I have tried multiple different manufacturer SFPs and it still does not get recognized.  I have compiled the new Intel driver but was hoping somebody could lead me to the documentation on including the driver on the MAAS PXE boot.  The intel NIC model is [COLOR=#333333][FONT=&amp]Intel X520-DA2 10Gbit sfp+.[/FONT][/COLOR]  If anyone else has seen this issue it would be helpful fro any feedback.

---

### Post by acneteng on 2018-03-27
I have solved this issue.  It was an issue that I was using an OEM SFP.  We purchased an Intel SFP.  This works with a Juniper QFX interface.

---

### Post by mörgæs on 2018-03-27
Good, please mark the thread solved.

---


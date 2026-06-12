---
title: "Using smartctl with Samsung F4 EcoGreen drives may result in data loss"
date: 2011-10-30
forum: Server Platforms
---

### Post by Vegan on 2011-10-30
WARNING: Do not use smartmontools with Samsung HD155UI and HD204UI drives unless the firmware patch is already installed. 

    Samsung provides separate patches for HD155UI and HD204UI and for HD204UI/JP. 

    This warning also applies to other tools which use IDENTIFY DEVICE to obtain drive information. The problem is not SMART related. 

    The problem could (at least) also be reproduced with hdparm (on Linux and Windows) and with SeaTools for Windows. 

    THE SAMSUNG FIRMWARE PATCH DOES NOT CHANGE THE FIRMWARE VERSION NUMBER (Believe it or not!). 

    Update: According to Samsung Support, HD204UI drives manufactured December 2010 or later include the firmware patch (see smartmontools-support mailing list). 

    Smartctl 5.39.X and 5.40 print a warning if the user has done a drive database update after 2010-11-24. 

    The warning will also be printed when the patch is already installed!

---


---
title: "Ubuntu 18.04.5 server installer crash on Dell"
date: 2021-06-25
forum: Server Platforms
---

### Post by lacid2 on 2021-06-25
My Ubuntu 18.04.5 installer is keep crashing on a Dell PowerEdge M630.
The crash happens a few seconds after I hit "done" at the VG/LV/HDD setup, I tried different settings, no changes. I had a different OS running before without issues. 
Any ideas?

[ATTACH=CONFIG]288728[/ATTACH]

---

### Post by MAFoElffen on 2021-06-25
I have a lot of Dell Poweredge Servers... LOL

On that model, 
 - Which chassis are you using with how many installed nodes? 
 - What boot options do you have set in BIOS? BIOS or UEFI Boot? 
 - What Drive controller and what drive types are you using? If the  PERC H330 or PERC 730(P) are you doing Non-RAID members, a hardware RAID array, or have the individual drives set as individual (single disk) RAID0 member passthroughs?
 - On the HDD settings what type do you have the drive type set to? In the BIOS options, there is a SATA Settings section, but also a section in the IDRAC for drive types. (I think I remember that being under device settings)

*** Make sure your BIOS and PERC firmware is up to date. There were 4 updates to PERC, that resolved things that could cause what you described. In the change log for the BIOS updates, one change in specific resolved Linux Boot problems, so that one in important to you now. If you log into Dell Support with your Service tag#, it will point you right there.

On the (BIOS) Setup Main Menu > System BIOS > System Security > Secure Boot Custom Policy Settings. Turn off/disable.

---


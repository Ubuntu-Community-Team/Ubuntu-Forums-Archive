---
title: "Dell PE 1950"
date: 2010-11-16
forum: Server Platforms
---

### Post by gmlinek on 2010-11-16
I have a DELL PE1950 that I am trying to configure a 3rd DC on. I have initialized the drives, and performed a consistancy chek on the volume. When I run the System Assistant on the server it comes back that the drives have not been "initialized". Is there something I am not doing?
 
Thanks,
Gary :(

---

### Post by tgalati4 on 2010-11-16
Set up RAID using RAID BIOS.  Probably Control-S at bootup.  I have a 1750.  I simply set up the drives in the RAID BIOS configurator and they were seen by the Hardy Server installer.  I'm not familiar with the term 3rd DC.  It's possible that the System Assistant relies on an older filesystem toolset that doesn't work with hardware RAID.

---


---
title: "Can a Windows guest be color calibrated for a correct color display ?"
date: 2015-05-19
forum: Virtualisation
---

### Post by whitebox on 2015-05-19
Hi

I am thinking to use KVM on my laptop and run Windows 8.1 as guest. 

I use lightroom to edit my photo and in photo editing, getting the display calibrated is the first step before you even start editing your first photo. 

It was straightforward when you run your OS in the normal way... you can just calibrated your display using hardware calibration or use free software to do a eyeball calibration... either way at the end you get a new icc profile and use it for the vga card. 

Had tried to google but only manage to find some hints related to virtualbox and vmware....  


[https://communities.vmware.com/message/1619581](https://communities.vmware.com/message/1619581)

[https://forums.virtualbox.org/viewtopic.php?f=8&t=18188](https://forums.virtualbox.org/viewtopic.php?f=8&t=18188)

It is still unclear to me whether a Windows guest under KVM be color calibrated for a correct color display ?

edit:

[https://communities.vmware.com/message/800567](https://communities.vmware.com/message/800567)

this link mentioned the vmware virtualized video card cannot support Lookup Table (LUT) installation... my second question is that even if the virtualized video card support LUT installation, will there be another layer of color correction at the host layer? If so, this will mean the color will not be correct again..

---

### Post by whitebox on 2015-05-19
after some thought I think my second question of whether will there be double color correction is irrelevant as long as i can calibrate the guest display , but of course it must be done in enlarged display or full screen.

---

### Post by Frogs Hair on 2015-05-19
There is some documentation, but I don't know if it's applicable.   [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

---


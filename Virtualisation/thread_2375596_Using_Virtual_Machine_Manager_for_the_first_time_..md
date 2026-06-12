---
title: "Using Virtual Machine Manager for the first time ... Please help"
date: 2017-10-25
forum: Virtualisation
---

### Post by linuxyogi on 2017-10-25
When I click on Forward


[ATTACH=CONFIG]277274[/ATTACH] (Click to enlarge)

I get this 


 [ATTACH=CONFIG]277273[/ATTACH]  (Click to enlarge)

---

### Post by linuxyogi on 2017-10-25
I have made some progress. Now I am stuck at 

[ATTACH=CONFIG]277275[/ATTACH] 
(Click to enlarge)

EDIT; Now after some tweaking I have managed to install Win7 but the resolution is very low. Any solutions ?

---

### Post by KillerKelvUK on 2017-10-26
Hi linuxyogi, well done on solving your initial problems.

Regards the low resolution in your windows guest please make sure that the video device you've specified for the windows guest configuration is set to 'QXL' for the model.  Then once you are in the guest you can install the windows driver for that virtual video card which will give you better resolutions as needed.  You can download the drivers from here [https://fedoraproject.org/wiki/Windows_Virtio_Drivers](https://fedoraproject.org/wiki/Windows_Virtio_Drivers), or if you are intending to use Spice as the display access protocol then I'd recommend you grab this ([https://www.spice-space.org/download/windows/spice-guest-tools/spice-guest-tools-latest.exe](https://www.spice-space.org/download/windows/spice-guest-tools/spice-guest-tools-latest.exe)) instead which will do pretty much the same as the virtio driver download but as a single install as well as enabling dynamic resolution scaling inside the spice client viewer.

---


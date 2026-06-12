---
title: "vSphere 6 and Ubuntu 04.16 - Unknown Display"
date: 2016-06-11
forum: Virtualisation
---

### Post by mode3 on 2016-06-11
Hello,
i am using latest vSphere and Ubuntu 04.16 Server with installed ubuntu Desktop.
Using vSphere Client console i have a low resolution 800x600. I can not change it because Ubuntu Display app tells me "unknown display".
open-vm-tools  and open-vm-tools-desktop  are installed.
What can i do to setup the display?

Regards

mode

---

### Post by MAFoElffen on 2016-06-15
As far as I know, open-vm-tools stopped working and has issues with vSphere 6.0 and Workstation 12 Pro. (maybe back in January/February?) This issue started with Ubuntu 15.10 and the releases of those two product versions. VMware support recommended using their own "VMware Tools." In this respect they are correct. This has worked fine this way for Ubuntu 15.10 and Ubuntu 16.04 for both vSphere (ESXi) 6.0 and Workstation 12. This works fine for me in vSphere.

From my vSphere Server:

From vSphere Client > Select/highlight the VM > Rightclick on the VM name > Select Open-Console ...

In the opened Console Window > Select Start.

With the VM running > Select the console windows "VM" menu option > Select "Install /Upgrade VMware Tools."

Shutdown the VM. > Start it back up.> Click in an open spot on your Guest desktop > Press <Cntrl><Alt><T>

In the terminal window:
```

xrandr -q

```
Confirm that your output shows modes above 800x600...

I have to do this before adjusting my VM guest resolutions.

---


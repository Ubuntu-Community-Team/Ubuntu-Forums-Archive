---
title: "Input lag with Wayland under VMWare 12"
date: 2017-09-05
forum: Ubuntu Development Version
---

### Post by cmccauley on 2017-09-05
Just updated a 17.05 Gnome Edition to 17.10, upgrade went very smoothly but I'm getting serious input lag on keystrokes in console apps like Terminal, Terminator and Tillix when running Gnome under Wayland; switching back to XOrg removes the lag.

I have other VMs running fine concurrently with the upgraded 17.10 (15.04 and a 17.04).  Perhaps a problem with Wayland under VMWare?

---

### Post by amano on 2017-09-05
-EDIT POST: oops, I missed the **VMWARE** part....

It could be some compatibility issue with vmware and libinput. Zesty used synaptics and Artful uses libinput.

On plain Artful i cannot see any input lag.

---


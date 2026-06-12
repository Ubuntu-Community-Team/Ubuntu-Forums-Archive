---
title: "VMware wont full screen."
date: 2007-12-22
forum: Virtualisation
---

### Post by seldomridgej on 2007-12-22
I have windows xp setup in VMware, with vmware-tools installed.  The display adapter shows up as the vmware adapter. When i try to fullscreen VMware, i get this error message:

Unable to find an appropriate host video mode.
Adding the guest mode to the 'display' subsection of the 'screen' section of your /etc/X11/XF86Config and restarting X is likely to help.

Failed to switch to full screen SVGA mode.

Anyone have any suggestions?

---

### Post by fjgaude on 2007-12-22
In the VMware menu, go to Host/Preferences/Display and check both options. From there you get auto sizing of screens.

---


---
title: "Ubuntu guest, VMware, VAIO, can't get max screen resolution"
date: 2009-09-07
forum: Virtualisation
---

### Post by kennedyjch on 2009-09-07
Have Sony Vaio VGN-Z46GD running vmware server. Have Ubuntu 9.04 installed and cannot seem to get max screen resolution of 1600x900. I only get 1440x900.

1) Any clues how to solve?
2) Is this more of a VMware question?

TIA

---

### Post by kennedyjch on 2009-11-13
Clarification: 9.10 run from CD (no install) works with full screen area; same installed in vmware virtual machine is limited to the smaller screen size. So it looks like it is a vmware limitation.

---

### Post by fjgaude on 2009-11-13
Did you install the VMware Tools?

---

### Post by kennedyjch on 2009-11-13
Yes. So I have Vista host with VMWare server and Ubuntu 9.10 guest. When I install under the VM, screen is limited to "standard" sizes (e.g., 1440 x 900, etc.) 

When I run from the live CD, I get the full VIAO screen resolution of 1600x900.

---

### Post by fjgaude on 2009-11-13
Uner the VM you have a software emulator for the video adapter. I never did get the VMware Tools to be installed under 9.10... kept droping off line at the same point in the Tools install from the command line.

---

### Post by kennedyjch on 2009-11-17
However I was able to get 9.10 to install under VirtualBox with the proper screen size (of course only when guest additions installed). 

However, runs REAL slow (I have 64 bit Vista host and 32 bit guest).

---


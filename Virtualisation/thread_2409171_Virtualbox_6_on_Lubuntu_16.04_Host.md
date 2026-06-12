---
title: "Virtualbox 6 on Lubuntu 16.04 Host"
date: 2018-12-28
forum: Virtualisation
---

### Post by treeant342 on 2018-12-28
Morning All:

I am guessing that Virtualbox 6 does not support Lubuntu 16.04 as a host but cannot find anything regarding this (anywhere).

I installed VirtualBox-6.0.0-127566 (and VirtualBox_Extension_Pack-6.0.0-127566) in Lubuntu 16.04 (x64) via command line (in a Root Terminal), without any problems.

I created a Windows 8.1 Pro (x64) VM as guest and it works fine (unless you want drag and drop, shared clipboard, shared folders or shared USB) in which case none of this works.

I tried installing the guest additions from within the Guest but as soon as it tries to install the WDDM driver, the screen goes black and does not come back making the VM useless.

Any thoughts on this would be great...

Cheers

---

### Post by ajgreeny on 2018-12-29
I have Xubuntu 16.04, still with the 4.4 kernel series, as host running VBox 6, as well as Xubuntu 18.04 on another machine, both with both Lubuntu 18.10, Debian 9.5, Windows XP, and Windows 7 guests running with no problems.

The Guest extensions pack is installed in all guests, so I wonder if you have some invalid settings in the guest VMs or the extension pack is not properly installed in the guests.

How did you install the guest additions in each guest?

In VBox 5.2.22, I found that Windows guests automatically installed the additions when the pack was added from Devices menu of the VBox manager window menu (at the bottom in my full screen guests), but that does not happen in VBox 6; in that version I have to open the GA folder in Windows explorer and run the .exe installer manually with a double click.

In the Linux guests I mount the GA .iso in its virtual CD, open a root terminal and drag the VirtualBoxLinux-xxxxxx.run script into the terminal and it installs without any difficulty.

---

### Post by treeant342 on 2018-12-29
Thanks for the response AJ
How do you verify that the extension pack is properly installed in the Guest?
The GA was installed from within the Win 8.1 Pro Guest (Devices-->Install Guest Additions CD)...
The script runs but the screen goes black as soon as the WDDM driver is installed so you cannot see anything (no amount of waiting brings it back) even after an ACPI shutdown, the screen is black on restart.
Also the snapshots tab is missing in the v_Box manager????
The only option is to clone the machine????????
Never had luck with V_Box on Lubuntu Host EVER...
They really need a better user manual or a tutorial-->suck
Thx

---

### Post by ajgreeny on 2018-12-30
Well, I don't know what is stopping the WDDM driver installation from completing on your guest as it does in mine.  Are you using graphic card drivers for the guest or simply letting the guest use the virtual hardware by default?  All my guests use the virtual graphics hardware, and I disable both 2D and 3D acceleration in the guests.

Thanks for the comment about snapshots tab being missing; I had not noticed that so will now do a search in the VBox forums to see what's going on with that and also if there are known problems with WDDM drivers.

---

### Post by ajgreeny on 2018-12-30
I've looked for the snapshot solution and it is now found by highlighting the VM in question in the left pane, then clicking on the "hamburger" style icon that appears beside the VM's name, which gives you Details, Snapshots & Logs, as shown in my screenshot.

I can not find anything about the WDDM drivers that is related to your problem.

---


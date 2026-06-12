---
title: "Cannot display graphical console type 'spice' no module named SpiceClientGtk"
date: 2013-07-17
forum: Virtualisation
---

### Post by DrJohn999 on 2013-07-17
Fresh install of 13.04 with qemu/kvm, virt-manager, virt-viewer, spice-client-gtk and others installed. Made newly-minted VM using previously existing LVM drive image. Windows 7 VM displays fine on VNC/VGA but the titled error message occurs if the VNC display is replaced in virt-manager with Spice display and Video qxl. Also in that case virt-viewer fails to connect to the display as well. Hoped this one was fixed in Raring, but maybe not. Any thoughts are much appreciated. Meanwhile, back to VNC.

---

### Post by wolfgang-zukrigl on 2013-11-22
I found this (german), which worked for me: [http://yrrgarten.de/2013/02/windows-7-in-der-kvm-unter-ubuntu-linux/](http://yrrgarten.de/2013/02/windows-7-in-der-kvm-unter-ubuntu-linux/)
sudo apt-get install spice-client

To connect to the running guest, type in a terminal 
spicec -h 127.0.0.1 -p 5900

---


---
title: "how do install nVidia drivers in a Ubuntu VM?"
date: 2008-12-20
forum: Virtualisation
---

### Post by eival on 2008-12-20
i recently installed Ubuntu as a VM on a Windows OS but it doesnt recognize the restricted drivers automatically and when i download the driver from nvidia.com it doesnt let me run it.

unless im not doing it correctly.

ive tried double clicking the file and also using sudo apt-get (draging the file into the terminal)

but neither work.

---

### Post by b0b138 on 2008-12-20
The video card of the VM is not your physical card, its an emulated basic vga/vesa card. The best it can do is installed with the guest additions (with vbox, vmware tools with vmware)

---

### Post by eival on 2008-12-21
well is there any way to get a larger resolution than 800x600 with an Ubuntu VM? 

cause i also have a Windows XP VM an it lets me go up to 1024x768

---

### Post by Dedoimedo on 2008-12-21
Hello,
You will have to install guest addons, for VMware: VMware Tools, for VirtualBox: Guest Additions. That's for two most popular desktop virtualizations tools.
Dedoimedo

---

### Post by eival on 2008-12-28
thanks Dedoimedo:popcorn:

---


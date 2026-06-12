---
title: "Run Ubuntu from a USB in a VM"
date: 2019-11-17
forum: Virtualisation
---

### Post by hcphoon01 on 2019-11-17
I have Ubuntu installed in a partition of a USB and I would like to know if it could be run from within a VM so I dont have to constantly restart my computer to swap between Ubuntu and Windows.


I've tried to follow the instructions in [this post]("https://askubuntu.com/questions/693719/how-to-boot-from-a-usb-drive-in-virtualbox") but I there is no bootable drive found when I try to select my USB.

---

### Post by crip720 on 2019-11-17
If you have enough ram, it is doable.  It might be easier to have a downloaded Ubuntu ISO on your computer and install ubuntu to VM from that.  Think most VMs would need extra packages to read/boot from USB(not sure).  Should have over 4GBs of ram for it to work well.

---

### Post by ajgreeny on 2019-11-17
You can certainly do this and many users do so, either your way or in the completely opposite direction, ie using Windows as the guest OS in a Linux/Ubuntu host.

There are many ways to run VMs but probably the easiest is VirtualBox, which I use.
Download the most recent version 6.0.14 from Oracle [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads) and install it, then also download the Extension Pack from the same webpage and install it by double clicking in the file manager.

Now download if necessary the iso image of the *ubuntu you want (you may find one of the alternative DE versions better as a VM than default Ubuntu) which you can now use when creating a new VM.

This is not the place to try and give you all details of using VBox, but there is a huge amount of info at [https://www.virtualbox.org/wiki/End-user_documentation](https://www.virtualbox.org/wiki/End-user_documentation) which you can search.

---


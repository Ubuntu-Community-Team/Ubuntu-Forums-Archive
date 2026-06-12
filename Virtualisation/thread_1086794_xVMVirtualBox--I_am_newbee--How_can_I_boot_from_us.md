---
title: "xVMVirtualBox--I am newbee--How can I boot from usb ???"
date: 2009-03-04
forum: Virtualisation
---

### Post by hoboy on 2009-03-04
I will like to boot from my usb.
I have installed Sun xVMVirtualBox, I have create a test virtual machine.
I have pluged my usb in the my computer the virtualBox detected it, I also have ubuntu-8.10-desktop-amd64.iso file on the usb, bu when I hit on start of the virtualbox instance i get the following error:
Fatal: No bootable medium found ! the system halted.

---

### Post by williane on 2009-03-04
if you have an ISO then just mount it through the cdrom option. shouldnt matter if its on your usb stick or not. theres no reason you should need to boot off USB in this case and im not sure if you can with Vbox.


edit: actually if youre using the iso on your usb drive you might want to disable usb in virtualbox. it might try resetting the port or something when it powers on and mess up the installation. i'm not sure on this just saying it could be an issue if you have problems mounting an iso on USB

---


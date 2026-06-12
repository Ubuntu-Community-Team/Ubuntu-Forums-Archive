---
title: "Mouse scrolling issue Ubuntu 18.04 LTS"
date: 2018-07-23
forum: Virtualisation
---

### Post by stardawg on 2018-07-23
Win 10 is host and Ubuntu 18.04lts guest.

Using VMware mouse i get scrolling issue where I have to scroll slowly to make scrolling smooth. If i scroll fast, the guest is trying to keep up and there is a big delay sometimes about 3-4 seconds before it registers the scroll. In win7 guest performance is fine, no scrolling issues.

I tried using my logitech g102 host mouse in guest and then the scrolling issue is fixed but the pointer is very laggy/jerky. Once i connect the host mouse(logitech g102) the cursor hand remains in the center of the screen and also I cannot use my keyboard.

I have tried in virtualbox as well I have a similar issue where If i disable mouse integration then connect host mouse to guest the mouse cursor just disappears so its even worse. I have also tried linux mint cinnamon tara on both VMWare and Virtualbox same problems. I have followed the release notes to make sure ive installed the correct version of Guest additions on virtualbox and installed open-vm-tools-desktop on VMWare. I have seen fixes involving disabling 3d acceleration and then restarting, using evdev instead of libinput however I cannot find a fix. 

I have enabled SVM in bios, disabled hyperv in windows and enabled the relevant sections for virtualisation in both vbox and vmware.

Any input would help a lot, thanks in advance.

---

### Post by stardawg on 2018-07-23
Installed Linux Mint 17.3 Rosa Cinnamon 64-bit and in the setup removed USB and printer from list in VMWare when creating a new machine, installed open-vm-tools-desktop. Works good so far, no laggy scrolling! SO I dont know if its the old linux or removing usb from list, either way it works, thansk to Linux Video Tutorial on youtube.

---


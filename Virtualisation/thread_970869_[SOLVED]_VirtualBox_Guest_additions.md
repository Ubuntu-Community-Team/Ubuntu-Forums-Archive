---
title: "[SOLVED] VirtualBox Guest additions"
date: 2008-11-04
forum: Virtualisation
---

### Post by detroit/zero on 2008-11-04
You'll have to pardon me - I seem to be mildly retarded.

I'm using Ubuntu 8.04.1, running VirtualBox 2.0.4 with a WinXPsp2 VM.

I have my XP install complete, and it works fine. Now I'm to the point of adding the Guest Additions. I don't see a link for it at the [VirtualBox downloads page]("http://www.virtualbox.org/wiki/Downloads"). I saw a post in here that said when you click Devices> Install Guest Additions from the VM window, it mounts a device in your virtual machine that allows you to install the additions. I clicked Devices>Install and opened My Computer to look for the device, and there was a D: drive mounted, however, it was 579 bytes big and only gave an inaccessibility error message when I double-clicked it.

Where do I get the guest additions package? When I was doing all this under Gutsy and I have the older VirtualBox, the tutorial I followed gave a link to a guest additions .iso file that I was able to mount under the CD/DVD tab in the settings for the VM. I've not been able to find a similar download link for the current version of VB.

Thanks

---

### Post by Nostalos on 2008-11-04
Click on Devices in the Menu bar, then "Install Guest Additions".  It will automount the ISO file.   And if your XP has autorun turned on it will automagically start the installer.

---

### Post by detroit/zero on 2008-11-04
Right.. that's what I meant when I said that method didn't work.

What I ended up stumbling upon was in the Settings tab for the VM, under the CD/DVD tab where you have the option to mount an .iso as a CD or whatever - it gave me a default option of the guest additions .iso located in /usr/share/virtualbox

Problem solved. Thanks anyway.

---

### Post by Nostalos on 2008-11-04
DUH!  Brainspaz on my part.  Glad you got it working.

---


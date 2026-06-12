---
title: "VMWare server catch 22"
date: 2008-01-14
forum: Virtualisation
---

### Post by Yadda on 2008-01-14
Hey there, I'm having a problem booting my XP raw partition from within VMWARE server. When I open the VM and boot the VM I am able to select my XP partition in grub but as soon as XP boots my mouse and keyboard do not function. I think that VMWare tools will fix this but I am unable to get into windows because it asks for product activation before the windows shell starts. I have searched the forums and have found solutions to each of the problems but, in this case, I can't install VMWare tools because I can't activate and I can't activate because I can't install VMWare tools... Any thoughts, anyone? Thanks!

---

### Post by KevinD_Atl on 2008-01-14
Make the Windows ISO bootable disk from the ISO in the VMware directory.  Once XP boots, go to Tools > Install VMware tools.  Without the disk in the drive, it will sit there and do nothing forever.  I think you have to restart the VMware Server and should be good after that.  I can't remember where those ISO's are stored, google it or my guess is the .var folder..?

---

### Post by fjgaude on 2008-01-14
You'll find the ISO images in /usr/lib/vmware/isoimages.

---

### Post by Yadda on 2008-01-14
Thanks for taking the time to reply. I'm not sure I understand what you mean though. I am still new to linux, I've been running it for only about a month now. I found the ISO in the /usr/lib/vmware-server/isoimages directory and burned it to a disk but it doesn't boot. I also mounted the ISO to the virtual cd-rom drive and still no luck. I have tried installing VMWare tools with the CD or ISO mounted and it still sits there and does nothing. I have tried restarting vmware and no luck there. I'm at a complete loss here :confused:

---


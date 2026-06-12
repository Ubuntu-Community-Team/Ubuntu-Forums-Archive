---
title: "Driver won't install"
date: 2008-10-17
forum: Virtualisation
---

### Post by Valok on 2008-10-17
So I've got my virtual machine up and running and everything is working fine except for the sound.  At first it couldn't detect the sound card, then I added one to the VM general settings.  Now it detects it, but with no drivers.  So I went ahead and downloaded some drivers and went through the whole installation process(without any errors popping up), then restarted my computer.  But there was no change, it still says that there are no drivers installed.  

I've tried installing the drivers a few times now but to no avail.  I still have no sound and I'm out of ideas.  If anyone's ever had a similar problem or knows of other things to try I'd love to hear 'em, thanks!

---

### Post by Shazaam on 2008-10-18
VMware? VirtualBox?
If VBox install Guest Additions to the guest.
If VMware Server/Workstation install VMware Tools to the guest.
Normally you shouldn't have to install any extra sound drivers to a virtual machine.

---

### Post by Valok on 2008-10-18
I am using Vmware 1.06, I've already installed the tools package to the guest, but its still saying that it can't find my soundcard.

I just noticed that the usage of 65-bit vista, or any vista for that matter on VMware is noted as experimental.  Maybe that could be part of the problem.

---


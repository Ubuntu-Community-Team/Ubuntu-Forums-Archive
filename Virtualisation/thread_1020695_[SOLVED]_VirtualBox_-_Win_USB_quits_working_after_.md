---
title: "[SOLVED] VirtualBox - Win USB quits working after exit"
date: 2008-12-24
forum: Virtualisation
---

### Post by jackmetal on 2008-12-24
I've got a strange problem that I'm trying to track down.  

I'm running Ubuntu 8.10 and VirtualBox 2.1 with numerous virtual machines.  

I'm running a Windows XP Virtual Machine for work connectivity (VPN, etc).  USB works fine when I initially start up my Virtual Machine (WinXP).  I can access my usb smart-card for VPN access and everything works perfectly.  If I shutdown the WinXP VM and start it back up again, I can no longer access the USB smart-card.  I've tried disconnecting and reconnecting it as a device while the VM is running; I've tried unplugging and replugging it into the USB, etc..  It will not recognize it again until I reboot my Host system.  Then, it works perfectly again until I shut that WinXP VM down again.

It not really that big of an issue, but I'd rather not have to reboot my Host system every day if I didn't have to.  I would rather just keep my Host running and be able to start and stop my WinXP VM for work, whenever I needed (without having to reboot to get it to work again after a VM shutdown).

It's got me stumped at the moment.  Any Ideas?

Thanks!!

---

### Post by jackmetal on 2008-12-24
A little more information as I troubleshoot the issue further:

Other USB Devices still work fine after a reboot of the WinXP VM.  It appears to only be the USB Smart-Card used for VPN access, which doesn't work after a reboot of the VM.

---

### Post by jackmetal on 2008-12-24
OK, I've found a 'work-around', but it would still be nice to find a true fix.  Here it is, in case anyone else runs into this issue:

If I unplug the USB Smart-Card after I shutdown the WinXP VM, and then plug it back in after I restart the VM, it will work without having to reboot the Host machine.  

It would be nice if I could just leave it plugged in all the time, but at least this appears to be a work-around for the issue in the meantime.

---


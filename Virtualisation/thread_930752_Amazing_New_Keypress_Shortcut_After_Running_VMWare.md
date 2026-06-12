---
title: "Amazing New Keypress Shortcut After Running VMWare"
date: 2008-09-26
forum: Virtualisation
---

### Post by pingnak on 2008-09-26
So, after quite a while of not using VMware, I try to use it again.

Do the usual 'vmware_config' thing to get it sorted out, and run it and everything seems to work fine...

Except any application I run from Gnome after the virtual machine is booted, if I press ANY key in its focused window, it instantly aborts (window disappears - do not pass go, etc.)  And the whole system stays that way AFTER I close VMWare, until I reboot.  Then all is well again... until I run VMWare.

So, I upgraded vmware to the latest, greatest version, re-did the whole setup thing.  Same problem.

So, I notice I'm still running 8.04/2.6.24-16-generic kernel.  OK, easily sorted out.  I go in, monkey with grub to load the 2.6.24-19-generic one that's already sitting there, reboot, rebuild 'envy', reboot, re-configure vmware, reboot, and up it pops... and it seems to work OK, and other apps don't crash when I launch them and type in them.  

Except today it did it again.

So I try to go to VMWare's web site to report a bug.  Well, it seems that the brilliant people at VMWare don't have a 'bug report' mechanism after your complimentary 30 day support contract runs out.  I'm not going to PAY for the @^&* 'privilege' of telling them their software is buggered.

I'm easy.  VirtualBox works OK and I already have more or less the same virtual machine running under that.  I think I'll just carry on using VirtualBox.  

I knew there was a reason I stopped using VMWare.  Just needed a little reminder, I guess.

---


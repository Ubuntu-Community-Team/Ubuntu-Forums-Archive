---
title: "[SOLVED] Bluetooth help"
date: 2008-11-15
forum: System76 Support
---

### Post by Lee_Machine on 2008-11-15
So I went out and bought a travel size bluetooth mouse for my Pangolin and I've heard many great things about the fixes in bluetooth in Ubuntu.

The mouse is a Logitech Bluetooth mouse.

Well I cannot get mine to work. I made sure that its not turned off in both the sessions and services menus.

I just couldnt figure it out. I ran that command sudo hcitool scan and i get the error Device not available: no such device. 

Note I had this same error about a year ago and that was because my bluetooth dongle took a dump on me.

So I looked in the device manager "which has to be installed" and i found out that bluetooth in my laptop is hooked into a USB port, not onboard. Is this correct S76?

Under the USB Hub and Bluetooth Adapter there is a warning that says "Inusfficiant power to operate USB device" 

I then thought it might be a powertop interference bug, so not wanting to go through the config file I just did a sudo apt-get purge powertop 

Nope, that didnt fix it. even did a reboot.

It did work once when I did nothing different and then i closed the laptop, it went into suspend successfully, and came back about an hour later and the mouse wont work again.

Oh I also checked the mouse on a dektop with Ubuntu 8.04 and a macbook. It works just fine on both.

thanks again for the help!

---

### Post by Lee_Machine on 2008-11-15
update:

I guess there is a bug in the bluez4 package with 8.10 so I followed the instruction at the bottom of this bug report 

[https://bugs.launchpad.net/ubuntu/+bug/289836](https://bugs.launchpad.net/ubuntu/+bug/289836)

It came back with quite a few bluetooth update and upon installing them I can now see bluetooth devices, but not pair.

You'd think I was a noob with all this issues i'm having. :lolflag:

I think that im just having bad luck and finding all the bugs in Ibex.

---

### Post by Lee_Machine on 2008-11-15
K I fixed the problem.

So KDE is not compatible with the Bluez4 stack and I had KDE-base installed for Amarok and for some reason kde network manager.

Even though I installed the bluez3 stack, which is being depreciated it didnt fully work and that's why I could see devices but not pair

So i purged all KDE packages and then all bluetooth device savings and everything works like it should. mouse works, obex works with another laptop and desktop, as does with my cell phone.

Good thing I dont like KDE :lolflag:

---


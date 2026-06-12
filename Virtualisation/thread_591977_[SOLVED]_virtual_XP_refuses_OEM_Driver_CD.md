---
title: "[SOLVED] virtual XP refuses OEM Driver CD"
date: 2007-10-25
forum: Virtualisation
---

### Post by brennydoogles on 2007-10-25
I recently Installed windows XP in Virtualbox on my dell E521, using the windows XP cd that came with the computer. However, when I attempt to install drivers from the driver cd, I get an error saying that the cd may only be used on dell computers. Is there a way to work around this and install the drivers manually from the cd? Any Help would be appreciated!

---

### Post by swisscow on 2007-10-26
Don't know about getting the drivers off the CD - you could download them off the net.

However have you considered that Virtualbox uses some virtual hardware, for example - the "graphics card" it uses is not the one that comes on your computer - it is a "virtual graphics card" (modelled on an intel I believe). So if you need graphic drivers (which you shouldn't) then the Dell CD won't help.

Not so sure about other hardware - I use Vbox on my laptop and added no other drivers to a basic xp install.

---

### Post by mysticmatrix on 2007-10-26
> **brennydoogles said:**
> I recently Installed windows XP in Virtualbox on my dell E521, using the windows XP cd that came with the computer. However, when I attempt to install drivers from the driver cd, I get an error saying that the cd may only be used on dell computers. Is there a way to work around this and install the drivers manually from the cd? Any Help would be appreciated!

I guess Guest additions include all driver deemed necessary.

---

### Post by Steve1961 on 2007-10-26
yep, the guest additions are all that you need.  The Virtualbox hardware is not the same as your real hardware.

---

### Post by jespdj on 2007-10-26
You do not need the OEM driver CD when you're running Windows in a virtual machine. So don't try to install it.

To Windows, the virtual machine does not look like the actual hardware it is running on. Instead of the drivers for the actual hardware, it uses special drivers from the virtualization environment.

Instead, install the VirtualBox Client Additions from the VirtualBox menu on your VM.

---

### Post by brennydoogles on 2007-10-26
Ok, that sounds fair enough. For a while I was getting really crappy resolution, but the addons fixed it up. Thanks!

---


---
title: "Running Linux and Windows simultaneously"
date: 2009-08-13
forum: Virtualisation
---

### Post by tamm on 2009-08-13
If I have 6 monitors and i want to run in 4 monitor linux and in 2 monitors Windows XP or 7. Both OS must run in full power and functions. common virtualization usually is like lite version but how do run both same time, will be controlled with one keyboard, mouse ect. Is possible to copy text and photos over one Os to other and open same files without sahring or coping one place to other.

---

### Post by veloce on 2009-08-13
> **tamm said:**
> If I have 6 monitors and i want to run in 4 monitor linux and in 2 monitors Windows XP or 7. Both OS must run in full power and functions. common virtualization usually is like lite version but how do run both same time, will be controlled with one keyboard, mouse ect. Is possible to copy text and photos over one Os to other and open same files without sahring or coping one place to other.

Are all monitors connected to just one box?  "full power" is only achieved by dedicated hardware.  In that case you use the "synergy" software to allow one keyboard / mouse to control all the machines. (No virtualisation involved).

A virtualisation solution is not going to meet your stated requirements.  The closest I would suggest would be kvm on an ubuntu host running all six screens (though I've never seen that done).  Use rdesktop (I use gnome-rdp) to bring up connections to a virtual XP.  The XP will be limited to one window - though you can have two XP vms running and have them on different screens.

Copying text between the os is supported by rdesktop but is a bit hit and miss - depends on the individual program.  I haven't tried pics but wouldn't expect much joy.

---


---
title: "virtualbox vista display driver"
date: 2008-04-08
forum: Virtualisation
---

### Post by -random on 2008-04-08
I've got virtualbox up and running in 7.10 and have both hardy and vista guests.

In vista i can do the shared folder thing...

BUT when i choose to 'update driver' and specify my graphics card (geforce 8600gt) vista doesn't select it :( Also the installer says "could not locate any drivers that are compatable with you current hardware"

Any ideas?

---

### Post by jespdj on 2008-04-09
When you run Vista (or any other OS) in a virtual environment (such as VirtualBox), then your hardware is virtualized. The guest OS (Vista) does not have direct access to the graphics card, and it doesn't see the real graphics card. Instead, it sees a virtual graphics card.

The virtual graphics card is not the same as your real NVIDIA card. The NVIDIA drivers for Vista do not work with the virtual graphics card, so trying to install NVIDIA drivers does not work.

So don't try to install the NVIDIA drivers in Vista, it won't work.

---

### Post by -random on 2008-04-10
Aaah, that's what i thought :(

So atm, all virtual machines emulate hardware without direct access?
 (exept maybe the motherboard/cpu that is)

 or is there a virtual macihne that can access my hardware?

---


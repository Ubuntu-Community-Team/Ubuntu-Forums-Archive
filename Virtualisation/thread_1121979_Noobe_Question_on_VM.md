---
title: "Noobe Question on VM"
date: 2009-04-10
forum: Virtualisation
---

### Post by nichos on 2009-04-10
I dual boot Ubuntu 8.10 / XPhomesp3.

If I install a VM in Ubuntu can I install & run MS Flight Sim in it? (or do I need to install XP as well).

thanx .........nick

---

### Post by lisati on 2009-04-10
I'm not overly familar with VM but offer this thought:
 If you're looking at using something like VirtualBox, you will usually have to use Windows within VirtualBox (or whatever your choice of virtual machine) before running a Windows program.

---

### Post by Therion on 2009-04-10
> **nichos said:**
> I dual boot Ubuntu 8.10 / XPhomesp3.

If I install a VM in Ubuntu can I install & run MS Flight Sim in it? (or do I need to install XP as well).

thanx .........nick
You would install VirtualBox and create a virtual machine with a "guest" operating system of Windows XP, which will require a regular Windows installation procedure (complete with re-entering your product ID, activation, updates, etc.) to complete.

Then you would have to install Flight Sim in the newly created virtual machine.  I don't know anything about Flight Sim, really, but if it requires DirectX to run you're pretty much outta luck.  Virtual Box does not support DirectX 3D acceleration.

---


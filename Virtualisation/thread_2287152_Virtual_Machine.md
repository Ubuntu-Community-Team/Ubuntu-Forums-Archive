---
title: "Virtual Machine"
date: 2015-07-17
forum: Virtualisation
---

### Post by chrsbrss on 2015-07-17
Here's my situation.

I've got some 3D software that I really enjoy using (Serif ImpactPlus5) and tried to use it in a virtual box.  

Got the virtual box installed on my Ubuntu computer, Installed XP inside virtual box and it's running great and even installed ImpactPlus inside of it, and running, but I'm not getting the graphics to work on it.  

Am I doing something wrong?

Chris

---

### Post by howefield on 2015-07-17
Thread moved to the "*Virtualisation*" forum. the application but

I don't know the application but you may need to install the (experimental) 3D Virtualbox drivers.

---

### Post by SeijiSensei on 2015-07-17
Make sure you have installed the Extension Pack: [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

Remember that the virtual machine is using a virtualized graphics adapter.  It may not have access to all the hardware functions of the actual graphics chip itself.  Even with the Extension Pack installed, you may find the graphics performance unacceptable.

---


---
title: "Create image of existing Win8 and install it in a Virtualbox within Ubuntu"
date: 2013-07-10
forum: Virtualisation
---

### Post by mlu17 on 2013-07-10
Hey guys,

I have a PC with 4 Harddisks. 2 of them build a raid where my data is stored.
On my SSD there is the Windows 8 System and on the 4th HDD there is Ubuntu installed.

I use my Windows 8 only for the Adobe products which don't run on Ubuntu, that's all.
So I asked myself if I can just create an Image from my Windows 8 SSD and install it as host system in a virtualbox on Ubuntu.

Is that possible? And if yes, what are the steps I would have to make?

Regards,
Michael

---

### Post by sudodus on 2013-07-11
If you have install media, you can install Windows into VirtualBox. Otherwise it is very hard, because Windows considers the virtual machine to be another computer, and refuses to run because the licencing limitations. Windows is not portable is the same way as Ubuntu.

See this link (browse the whole thread to find the relevant posts) [http://ubuntuforums.org/showthread.php?t=2119831](http://ubuntuforums.org/showthread.php?t=2119831)

---

### Post by xe1ufo on 2013-07-13
There isn't a way to start the already-existing Windows install in a Virtual Box?

---

### Post by Mark Phelps on 2013-07-13
I've read that there is a way to do that ... but it leads to a problem of activation/reactivation.  The VM is treated as a different hardware setup than the actual Windows install.  So, when you crank it up in the VM, you have to activate it.  But, when you later crank it up in native mode, that is seen as different hardware -- and you have to reactivate.  So, every time you switch back and forth, you have to reactivate.  In short order, Windows will REFUSE to reactivate because you've done that too many times -- which then leaves you with the inability to run it anymore.

---

### Post by JKyleOKC on 2013-07-13
In addition to this problem, it's also necessary to make major changes to the configuration of Windows, because the virtual hardware that will be used by the VM is drastically different from the actual hardware for which Windows is configured. This means possibly different video drivers, disk interfaces, and so on -- even though the physical hardware doesn't change at all.

Using the existing HD installation rather than a virtual disk is practical only for retrieving data -- and the "shared folders" feature in vbox makes it unnecessary for that.

---

### Post by mlu17 on 2013-07-15
Alright, thank you all for your answers. 

I guess I will stick to the dual boot option then to avoid any problems :)

Regards,
Michael

---


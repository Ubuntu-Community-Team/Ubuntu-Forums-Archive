---
title: "VirtualBox"
date: 2008-05-26
forum: Virtualisation
---

### Post by 1467 on 2008-05-26
i installed VirtualBox 2day using this tutorial [http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html]("http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html") got to the last step and when i click start i get (
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

)

---

### Post by p_quarles on 2008-05-26
Moved to Virtualization. 

Have you tried doing what the error message is *specifically telling you to do*?

---

### Post by 1467 on 2008-05-26
i think i need to create a /dev/vboxdrv how do i do that

---

### Post by p_quarles on 2008-05-26
```
sudo apt-get install virtualbox-ose-modules-`uname -r`
```
You will also need to add your main user to the appropriate group, if you haven't already:
[code]sudo adduser `whoami` vboxusers/code]

---

### Post by 1467 on 2008-05-26
thank you vary much

---


---
title: "[SOLVED] virtualbox wont run using 2.6.24-12"
date: 2008-04-09
forum: Virtualisation
---

### Post by bhuthogg on 2008-04-09
i had virtualbox up and runing but i have decided  to load the 2.6.24-12 kernal on boot so i have my xbox wireless controller working,

here is the error code i get 


The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by bhuthogg on 2008-04-09
sorry ignore this i just had to  sudo adduser MYNAME vboxusers

---


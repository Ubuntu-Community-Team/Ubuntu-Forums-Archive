---
title: "Mouse stopped working on Ubuntu VM"
date: 2024-01-15
forum: Virtualisation
---

### Post by newjoker on 2024-01-15
Hi,

I've been using Ubuntu 22.04.3 virtual machine on Windows 10 with VirtualBox 7.0.10 for some time and everything was good. But suddenly, the mouse stopped working properly. I can use the icons in the sidebar but I can't click on anything in opened windows. Interestingly, after opening a new app window, I can drag it but only once. If I try to do it again, nothing happens and I have to reopen the application. I have to close apps by right-clicking on their icons in the sidebar because I can't click the X button, among the others.


I've tried different solutions like:


- disabling and enabling Mouse Integration
- changing pointing device to PS/2 Mouse, USB Tablet or even USB Multi-Touch Tablet
- killing drag&drop processes
- unchecking Enable Nested Paging in Acceleration settings

but nothing helped. What else can I do?

---

### Post by TheFu on 2024-01-15
Reinstall the **Guest Additions**.
I haven't used vbox in over a decade, but it used to be that after every new kernel was installed into a VM, the guest additions needed to be reinstalled to relink to the new kernel.

---

### Post by newjoker on 2024-01-16
> **TheFu said:**
> Reinstall the **Guest Additions**.

Thanks for the reply. I've just tried that using the following commands:

sudo apt-get update
sudo apt-get install virtualbox-guest-x11

and restarted the virtual machine but the issue still occurs. Anything else I can try to fix it?

---

### Post by 80884b on 2024-12-04
I had a similar problem using virtual box Just after getting my VM running my whole laptop, froze up being able to only restart my laptop because of touchscreen and after restarting my laptop and deleting the VM my touchpad and mouse did not work properly. I had to do a factory reset to get my Laptopto work properly.

---

### Post by ajgreeny on 2024-12-04
The current updated version of VBox is 7.1.4; what version are you running and which version if the guest additions have you got installed?
It is essential that VBox and the GA are both exactly the same version or that sort of problem becomes more likely.

---


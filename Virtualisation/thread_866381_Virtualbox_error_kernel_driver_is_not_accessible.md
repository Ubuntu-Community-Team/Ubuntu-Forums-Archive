---
title: "Virtualbox error: kernel driver is not accessible"
date: 2008-07-21
forum: Virtualisation
---

### Post by kramer65 on 2008-07-21
Hello,

I just installed virtualbox, made a drive for windows, and now wanted to install windows. I first got this error that I needed to install some kind of virtualbox-ose module. So I did.

Now I get an error saying:

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).

Does anybody know what I should do here?

---

### Post by rogier.de.groot on 2008-07-21
Open up the management program for users & groups, add your user account to the 'vboxusers' group, logout & back in and you're set to go.

---

### Post by kramer65 on 2008-07-21
Great. That works!

I am just installing windows now. But it doesn't capture my mouse. It says it captured it, (green arrow icon in bottom left) but it actually hasn't. 

Do you happen know a solution to this as well? :D

---


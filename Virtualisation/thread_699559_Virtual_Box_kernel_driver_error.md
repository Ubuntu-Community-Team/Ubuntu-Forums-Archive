---
title: "Virtual Box kernel driver error"
date: 2008-02-17
forum: Virtualisation
---

### Post by Raccoon1400 on 2008-02-17
When I  start my virtual box virtual machine, I get a box with this error. However, I can start the virtual machine when I log into the root user account.



The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by kyphi on 2008-02-17
In a terminal type ```
sudo chmod 666 /dev/vboxdrv
``` then press Ctrl+Alt+backspace to restart X.  That will give you the necessary permissions.

Also check that you have been added to the vboxusers group.

---

### Post by Raccoon1400 on 2008-02-17
Thanks

---

### Post by Raccoon1400 on 2008-02-18
This works until my next reboot, but the changes aren't permanent, How do I make them permanent?

---

### Post by kyphi on 2008-02-18
Try this
```
sudo usermod -G vboxusers -a userid
sudo chmod 666 /dev/vboxdrv
```
The first line adds you to the vboxusers listing and the second changes the permissions for the vbox driver.

---


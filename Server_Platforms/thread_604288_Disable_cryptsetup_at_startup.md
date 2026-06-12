---
title: "Disable cryptsetup at startup ?"
date: 2007-11-06
forum: Server Platforms
---

### Post by Traxman on 2007-11-06
Hi,

The 7.10 works fine but i have a partition i want to mount
when im logged on. I have tried to disable this behavior 
and i guess its in the kernel since i can remove crypttab, renaming
the init.d scripts and it still asks me for the password at the boot.

Im lucky i have access to my machine via a kvm console but its
annoying that i need to use it every time i need to reboot the server.

Is there a way to disable the LUKS at startup so i can start the machine
and i can enter the password and mount it when i get logged on. I dont
want it to be auto mounted and stuff like that, its a partition i want to
open when im working on it.

Any suggestions would be nice )

** Update **

After installing a new kernel i saw it added cryptsetup so after some checks i moved the file /etc/initramfs-tools/conf.d/resume and 
updated the initrd with update-initramfs -u and it dident include anything with cryptsetup. After the update the system now
boots up without asking for password and i can open it and mount it when i get online )

Hope this can help others aswell that want one partition where they can mount when they like.

---


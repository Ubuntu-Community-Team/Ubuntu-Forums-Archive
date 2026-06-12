---
title: "File permissions"
date: 2008-05-29
forum: Virtualisation
---

### Post by krikuku on 2008-05-29
I am migrating to ubuntu 8.04 and I am currently doing a virtual machine setup. I am using virtualbox ose.

I have setup a virtual machine for backtrack beta 3. I had not changed write permissions for /dev/vboxdrv, so virtualbox displayed an error:

> 
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..

I did as told, and the virtual machine launched correctly without errors, until next power off.

Apparently ubuntu automatically resets the write permissions for /dev/vboxdrv at startup. (Bug?)

How do i permanently change write permissions for /dev/vboxdrv?

---

### Post by bluefrog on 2008-05-29
if you have added your user to the vboxusers group, there is no reason it shouldn't work.

---

### Post by krikuku on 2008-05-29
I had not added my user to the vboxusers group. I searched around a bit, and found a simple way to do so:

```
su [insert favorite text editor] /etc/group
```

```
 ...
haldaemon:x:123:
kristian:x:1000:
vboxusers:x:124:kristian
```

Thank you for the help!

---

### Post by bluefrog on 2008-05-30
the simple way is to use the tools made to do so.

graphically
syst/admin/users and group

command line
sudo gpasswd -a user vboxusers

---


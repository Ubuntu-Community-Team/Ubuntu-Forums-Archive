---
title: "help with virtual box"
date: 2007-10-20
forum: Virtualisation
---

### Post by nickdr on 2007-10-20
everytime i try to start virtual box i get the following error:

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE)

How do I fix this? I am trying to set up Windows XP as the guest, and this comes up everytime I hit Start in VirtualBox. I am runnning Vbox in Ubuntu 7.10 Gutsy 64 bit.

---

### Post by Colro on 2007-10-20
Put this in the terminal:

```
sudo gpasswd -a YOURUSERNAME vboxusers
```

Replace YOURUSERNAME with your user name, obviously ;p

---

### Post by Win2Mac2Linux on 2007-10-20
Of course the previous response using the terminal is faster, but being I am a still learning noob I happened to figure it out (all by myself I might add) by clicking on System-Admin-Users and Groups.  You'll then enter your password.  Click on "Manage groups" and scroll the list for virtualbox and click the box next to your name...

Granted this is a few more steps, but figured I'd add it in there for the rare time I actually get to contribute something...

---


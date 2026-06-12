---
title: "Problem with VirtualBox: Virtual vboxusers"
date: 2007-11-17
forum: Virtualisation
---

### Post by neonl on 2007-11-17
Hi.

I installed virtualbox to test other linux distros and to install windows 2000.

I installed by this method:```
sudo nano /etc/sources.list
*add the repo*
deb http://www.virtualbox.org/debian gutsy non-free
```then:```
wget http://www.virtualbox.org/debian/innotek.asc
apt-key add innotek.asc
```Everything is fine until I try to start the box I created, I get this:> 
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}



How can I handle this?

---

### Post by scorp123 on 2007-11-17
> **neonl said:**
> How can I handle this? [http://ubuntuforums.org/showthread.php?p=3766472#post3766472](http://ubuntuforums.org/showthread.php?p=3766472#post3766472)

---

### Post by ubukool on 2007-11-17
Hi,

There is a simple solution for this, you will be glad to know!

go to system -->Administration---->Users and Groups

click on 'manage groups'

Scan down the list, there should be a group called 'vboxusers'.  If there is, double click on it and make sure that your username is ticked so that you are a member of the group.  If there is no group, create one by clicking on 'Add Group', typing vboxusers in the group name field and making sure that your user name is ticked so that you are a member.  Then, log out and log back in again.  When you a start your virtual machine, everything should work!

Good luck!

:)

---

### Post by Leslie Viljoen on 2011-10-25
To be totally clear: if you are running an Ubuntu host AND guest, the user you run virtualbox under in the HOST needs to be added to vboxusers group in the HOST.

---

### Post by CharlesA on 2011-10-25
Wow, major necro.

---


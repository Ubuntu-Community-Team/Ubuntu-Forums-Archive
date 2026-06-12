---
title: "Windows host - Ubuntu guest ???"
date: 2009-08-30
forum: Virtualisation
---

### Post by Robotman on 2009-08-30
In the interest of safer browsing for a friend, I'm trying to set up a Windows XP laptop to run Ubuntu inside VirtualBox.  I've got VB for Windows installed, and Ubuntu 9.04 installed inside that.

Now I need to know how to install the "Guest Additions" software inside Ubuntu and get the host and guest desktops together as a shared folder for transferring files.

I've had VirtualBox download and mount the "Guest Additions" CD in my virtual Ubuntu, and now I need to know how to proceed.

Can anyone give me some detailed steps?

---

### Post by x33a on 2009-08-30
maybe this could help:

[http://tombuntu.com/index.php/2008/09/22/install-virtualbox-2-guest-additions-in-ubuntu/](http://tombuntu.com/index.php/2008/09/22/install-virtualbox-2-guest-additions-in-ubuntu/)

---

### Post by Robotman on 2009-08-30
Awesome! :D
Thanks for the link.  The line I needed specifically was:
```
sudo /media/cdrom/VBoxLinuxAdditions-x86.run
```
Now I can run the Ubuntu desktop in Seamless mode along with the Windows desktop.

Does anyone know how to set up a shared desktop between the host and the guest so I can transfer files from one to the other?

---


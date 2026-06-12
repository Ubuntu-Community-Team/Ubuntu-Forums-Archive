---
title: "connecting virtual os with each other"
date: 2011-08-13
forum: Virtualisation
---

### Post by nos09 on 2011-08-13
I have three virtual os. windows xp, slackware, Ubuntu.  and I want to know how do I share files between them.  make them server or client.
thank you in advance..

---

### Post by Johnb0y on 2011-08-13
what VM software are you using?

---

### Post by Johnb0y on 2011-08-13
you could have a look at:

VMware: [http://www.vmware.com/support/ws3/doc/ws32_running9.html](http://www.vmware.com/support/ws3/doc/ws32_running9.html)

[http://maketecheasier.com/sharing-files-between-ubuntu-host-and-virtual-machines/2007/12/17](http://maketecheasier.com/sharing-files-between-ubuntu-host-and-virtual-machines/2007/12/17)

[http://social.msdn.microsoft.com/Forums/en-US/servervirtualization/thread/a11a0b96-e5e9-4649-8c8c-9b66ddd0a2d3/](http://social.msdn.microsoft.com/Forums/en-US/servervirtualization/thread/a11a0b96-e5e9-4649-8c8c-9b66ddd0a2d3/)

or

[http://www.linuxquestions.org/questions/linux-networking-3/file-sharing-between-a-virtual-machine-and-the-host-machine-457763/](http://www.linuxquestions.org/questions/linux-networking-3/file-sharing-between-a-virtual-machine-and-the-host-machine-457763/)

---

### Post by haqking on 2011-08-13
Set up shared folders

---

### Post by geoff13 on 2011-08-14
set up shared folders and install guest additions by going to the device drop down menu... makes all your shares accessible through a vbox directory.

Also works as a great workaround for a lack of usb support!!!!

---

### Post by lmarmisa on 2011-08-15
Define the network interfaces of your VMs as bridged in the virtualization program and use CIFS/Samba for sharing files.

---


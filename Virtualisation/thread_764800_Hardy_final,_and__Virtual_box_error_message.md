---
title: "Hardy final, and  Virtual box error message"
date: 2008-04-24
forum: Virtualisation
---

### Post by landcross on 2008-04-24
On Hardy final, have been running Virtual box without problems on Hardy since first Alpha release.
On last upgrade  have start up problem with Virtualbox

This is the message. What commands do I need to use?


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).

This earlier posting from someone with a similar problem did not help.

I already exist as a member of the VirtualBox Group 

Go System>Administration>Users and Groups
Enter Root Password
Manage Groups
Scroll down to VirtualBox Users>Properties
Tick your login name
OK>Close>Close etc

RESTART

---

### Post by caver1 on 2008-04-24
Do as the error message says.
Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
works fine.
caver1

---

### Post by MikeAzores on 2008-04-25
> **caver1 said:**
> Do as the error message says.
Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
works fine.
caver1

Hi!
I'm getting the same message to. I tried what you said (I think you mean "start" instead of "setup") and I throws an arror saying something like can't find the correspondent kernel module of virtualbox.

How can I remove the Virtualbox OSE version on Hardy and install the VirtualBox Full edition? Do I have to compile it? I currently have a guest Operating System installed so I do not want to loose this.

Regards.

---

### Post by landcross on 2008-04-25
Regarding Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.

What commands do I need to use in the Terminal to do this?

I tried the above anfd got this message

sudo: /etc/init.d/vboxdrv setup: command not found

---

### Post by caver1 on 2008-04-25
Go to Synaptic and remove VirtualBox.
Then go here
 [https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.5.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.5.6-G-F@CDS-CDS_SMI)

pick the version you need download and install.

For Hardy I downed the Debian etch one. Its a deb file so all you have to do is install it.
caver1

---

### Post by landcross on 2008-04-25
I do not want to reinstall XP and other software again.

Is this necessary, it was running fine in earlier alpha & beta versions of Hardy.

Is there no other solution?

---

### Post by MikeAzores on 2008-04-25
> **caver1 said:**
> Go to Synaptic and remove VirtualBox.
Then go here
 [https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.5.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.5.6-G-F@CDS-CDS_SMI)

pick the version you need download and install.

For Hardy I downed the Debian etch one. Its a deb file so all you have to do is install it.
caver1
It worked. Thanks.

---


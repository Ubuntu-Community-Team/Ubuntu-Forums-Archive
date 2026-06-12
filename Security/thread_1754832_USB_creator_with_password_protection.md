---
title: "USB creator with password protection"
date: 2011-05-10
forum: Security
---

### Post by peterfoss79 on 2011-05-10
Hi all

I have been trying out various USB creator software in UBUNTU environment, but none of them offers to password protect the USB device when booting it.

My concern is that if I loose a bootable USB, somebody else might be able to load it live and access my files, emails, etch.

Any suggestion on how to password protect a bootable USB device?

Thanks

---

### Post by bodhi.zazen on 2011-05-10
Make a crypt in the free space.

The other option is to learn to use the live-build scripts and make a custom iso. There is the option to encrypt the iso.

---

### Post by BkkBonanza on 2011-05-11
If you're talking about having an encrypted usb filesystem that you can use in Ubuntu then I've used and can recommned **Truecrypt** for this. 

It allows you to format a device as an encrypted filesystem. When you mount the device it will prompt for a password or key file (or both if desired) and then it will be mounted just as any other filesystem. Truecrypt is easy to install from Synaptics (repos) and fairly easy to understand and use, and known to be very robust security wise.

---


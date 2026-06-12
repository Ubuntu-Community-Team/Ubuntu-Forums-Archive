---
title: "could not access hard disc in Ubuntu running in QEMU inside WinXP"
date: 2007-11-06
forum: Virtualisation
---

### Post by kagashe on 2007-11-06
I am running Ubuntu Live CD within Windows XP using QEMU as per instructions on pendrivelinux.com on thisp [page]("http://www.pendrivelinux.com/2007/09/18/run-a-live-linux-cd-from-within-windows/"):

I am able to see the Network Card eth0 and have setup the static IP, netmask, Gateway, DNS etc. as per the settings in Windows but could not browse the net,although, the Windows XP is presently connected to the net through the same card.

The internet connection is through cable and the login is through 24onlient client. I have the linux software of crclient on linux partition on the same PC, therefore, I tried to mount the drive but the Linux running in QEMU is unable to access the drives.

Is there any way to access the drives on the hard disc in the guest Linux OS running in QEMU on Windows XP.

---

### Post by Ian505 on 2007-11-06
I personally use [Qemu Manager]("http://www.davereyn.co.uk/index.htm") which makes qemu much easier to work with. I am not very good at virtualization stuff myself and I am sorry to say that this is all the help I can offer.

-Ian

---


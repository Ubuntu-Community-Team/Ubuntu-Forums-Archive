---
title: "Sun Virtualbox: Error While Installing Guest Additions in Ubuntu 9.10"
date: 2009-11-13
forum: Virtualisation
---

### Post by Nandus1 on 2009-11-13
Hello all,
I am running into an issue while trying to install guest additions on an "ubuntu-9.10-desktop-i386" guest on and a Windows XP host. Both operating systems are 32 bit.

I clicked on "Devices", "Install Guest Additions" and received the image without issue.

I opened the terminal and attempted to install as normal in an Ubuntu environment.
See below.

user@user-desktop:~$ cd /media/cdrom
user@user-desktop:/media/cdrom$ sudo bash ./VBoxLinux*
[sudo] password for user:
Verifying archive integrity... All good.
Uncompressing VirtualBox 3.0.10 Guest Additions for Linux installation................................................................................................................................................................................................................................
VirtualBox 3.0.10 Guest Additions installation
[COLOR="Red"]Detected unsupported x86 environment.[/COLOR]
user@user-desktop:/media/cdrom$

Any help would be greatly appreciated.

---

### Post by Nandus1 on 2009-11-13
Solved.
Ran the "autorun.sh" located in the mounted Guest Additions image.

Good to go.

---

### Post by wilee-nilee on 2009-11-13
Never mind, glad you got it working.

---

### Post by Nandus1 on 2009-11-13
Thank you for your intent to help. lol
I knew I had the correct OS versions and it was something with the syntax I was using. Thank God for autoruns.

---

### Post by wilee-nilee on 2009-11-14
I like the virtual set ups it is really quite cool, but they modify the kernel I believe and I am not enough of a Geek to know if this is actually the case or move the kernel to it's original code if I want to remove the VM.

---

### Post by Elep.Repu on 2009-12-16
> **Nandus1 said:**
> Solved.
Ran the "autorun.sh" located in the mounted Guest Additions image.

Good to go.

Thanks a bunch.

---


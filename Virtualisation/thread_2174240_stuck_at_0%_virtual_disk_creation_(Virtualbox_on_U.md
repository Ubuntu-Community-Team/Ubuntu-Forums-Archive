---
title: "stuck at 0% virtual disk creation (Virtualbox on Ubuntu)"
date: 2013-09-13
forum: Virtualisation
---

### Post by Coder88 on 2013-09-13
Installed Ubuntu 13.04 i386 on my laptop yesterday, installed virtualbox app using 'sudo apt-get install virtualbox' (I have used virtualbox and guest additions many times with Windows 7 as the host) to use linux as host with goal of Windows 7 client. So i clicked to have virtualbox create a fixed 40GB virtual drive (plenty of disc space, not an issue) at the default location in my home directory. The progress bar appears but just stays at 0%. What am I doing wrong? Am I supposed to 'sudo virtualbox' rather than just run it from Accessories in the menu? not mandatory that I do this, but I thought it would be fun to install a virtual Windows 7 machine with linux as the host.

---

### Post by sudodus on 2013-09-16
What you describe seems to the the correct way to do it. I don't know if there is a size limit. My biggest virtual drive is 20 GB. You can try with that size (and if necessary have two virtual disks for Windows (for example, you can have installed programs and your personal data on the second drive, if there is a size limit).

*Edit*: Virtualbox runs without superuser privileges. A free alternative is KVM, qemu and virt-manager according to this link[URL="https://help.ubuntu.com/community/KVM/VirtManager"]

https://help.ubuntu.com/community/KVM/VirtManager[/URL]

I think virt-manager needs superuser privileges.

---


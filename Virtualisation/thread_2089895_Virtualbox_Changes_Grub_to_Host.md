---
title: "Virtualbox Changes Grub to Host?"
date: 2012-11-30
forum: Virtualisation
---

### Post by bdentremont on 2012-11-30
I've just encountered a scary situation which I would not have thought possible.  My computer is working, but I would appreciate any insight into what might have happened here.

Yesterday night I installed Debian Squeeze into Virtualbox  The installation media was an iso image on an external hard drive which I mounted to the virtual machine.  Never burned a disk or extracted anything from the iso outside of the virtual machine.  During the installation into a clean virtual machine, I encounted a message from the Debian installer.  I can't remember the exact text, but it essentually was saying this was the only detected operating system on the computer and was wondering if I wanted to overwrite the boot loader.  I found this slightly strange since the Debian installer should have been seeing a clean virtual disk, but said yes.

While the Debian installer was finishing in the virtual machine, I launched my backup script (which creates a DAR archive on the external disk).  I mension this because it was the only sudo command that I think that I issued on the host system all night.

Today, I rebooted the host Ubuntu system and was absolutely stunned to see that my Grub2 kernel selection screen now changed to Grub 1.99 with a pretty Debian-styled background.  What happened?!

Host system: Ubuntu 12.04 (AMD64) on Macbook Pro 7.1 13"
Guest: Debian 6.0 (AMD64)
VirtualBox: "VT-x/AMD-V" and "Nested Paging" are enabled for this system

---


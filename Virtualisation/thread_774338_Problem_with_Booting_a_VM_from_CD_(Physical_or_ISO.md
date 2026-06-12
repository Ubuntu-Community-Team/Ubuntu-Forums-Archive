---
title: "Problem with Booting a VM from CD (Physical or ISO)"
date: 2008-04-29
forum: Virtualisation
---

### Post by buzzzzer on 2008-04-29
Hi All,
I have installed the Hardy amd64 edition on my Dell XPS [Intel Core 2 Duo 2.0Ghz). I was previously using Gutsy 32-bit edition with VMWare Server installed to run my Windows programs. Now with Hardy - i tried using VirtualBox but when using the existing VMDK (Virtual Harddisk) from VMWare - the virtual machine does not work - It freezes before even showing the initial XP Boot Logo.

I tried to do a fresh install from the ISO for Windows XP which i used previously. But the VM halted with "Could not read from the boot medium! System Halted". In the log it says "CDROM boot failure code : 0007"

I tried removing VirtualBox and adding QEMU but there also it was the same result and the same error code: "CDROM boot failure code : 0007". This ISO mounts well in Hardy using the -o loop option so it is not the ISO issue. Even i tried using the physical CD ROM and there also the same error.

Has anyone else encountered the same error????
Please help!!

---


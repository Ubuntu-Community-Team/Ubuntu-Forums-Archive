---
title: "Windows VM having limited privileges and no internet : dangerous ?"
date: 2023-10-13
forum: Security
---

### Post by tryphon2 on 2023-10-13
Hello,

I like the possibility to start a Windows virtual machine under Ubuntu with a common remote volume to share data.

Imagine this setup :  Windows 10 VM, user account with limited privileges, remote desktop activated, no internet access at all, smb access to one distant volume on a server. An administrator account also exists with a furiously long password. VM host (Ubuntu 20 or 22) has access to internet and local network.

Daily use this VM with Remmina from other machine on the local network (user account only) : is it dangerous ?

Thank you.

---

### Post by TheFu on 2023-10-13
All networked OSes are dangerous on some level.  Your level of risk and what you need to keep secure should determine how much security should be involved.

Long passwords don't really help for most remote attacks. Attackers find different ways in.  If you are using remote desktops and a VM, why bother with RDP?  Use the solution provided by the VM host.  You didn't mention which hypervisor is being used. It could matter greatly.  For example, I use KVM/Qemu on libvirt and have remote access from anywhere on my LAN even when the VMs don't have any networking enabled. It is through an ssh tunnel, by default, so it would be secure even over the internet, assuming my ssh credentials are key-based, never passwords.

---


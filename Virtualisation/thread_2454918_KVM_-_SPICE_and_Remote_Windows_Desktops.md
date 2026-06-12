---
title: "KVM - SPICE and Remote Windows Desktops"
date: 2020-12-08
forum: Virtualisation
---

### Post by rsteinmetz70112 on 2020-12-08
I'm interested in experimenting with secure remote windows desktops. 

Is it possible to run Windows in KVM and connect to a remote desktop from windows using SPICE (or some other secure method)?
I have an application I'd like to make available remotely but its Windows only.

Be gentle I'm just starting to try to figure this out.

---

### Post by CelticWarrior on 2020-12-08
As long as it has the proper network configuration you can use any VM the same way and for the same purpose as any other bare metal installation.

---

### Post by TheFu on 2020-12-08
I don't know about using Windows as the client viewng platform, but spice connections are tired to either an SSL layer or through ssh+qemu connection. The Windows guest VM needs to have the qxl and spice drivers loaded manually. In linux, those are part of the available kernel drivers.

I've posted my virt-viewer script here. a few times. But that is LAN only or on the same hardware. For remote connections over the internet, I use x2go. I have seen someone else oVirt with spice over the internet, but not with ubuntu.

Sorry, I'm not much help for your specific needs. I don't use Windows clients much.

---

### Post by rsteinmetz70112 on 2020-12-09
> **TheFu said:**
> I don't know about using Windows as the client viewng platform, but spice connections are tired to either an SSL layer or through ssh+qemu connection. The Windows guest VM needs to have the qxl and spice drivers loaded manually. In linux, those are part of the available kernel drivers.

I've posted my virt-viewer script here. a few times. But that is LAN only or on the same hardware. For remote connections over the internet, I use x2go. I have seen someone else oVirt with spice over the internet, but not with ubuntu.

Sorry, I'm not much help for your specific needs. I don't use Windows clients much.

It appears that x2go has a Windows client but can x2go display a Windows VM on a remote desktop? That question may require a deeper dive into x2go. I've also read that recent gnome desktops have compatibility issues.

---

### Post by TheFu on 2020-12-10
> **rsteinmetz70112 said:**
> It appears that x2go has a Windows client but can x2go display a Windows VM on a remote desktop? That question may require a deeper dive into x2go. I've also read that recent gnome desktops have compatibility issues.

No. The x2go server is linux only. It is not connected to qemu/kvm at all. What I do is to remote into a Linux desktop on the same LAN, then use any rdp client into the Windows VM. I haven't tried using a spice client from the linux desktop into the Windows desktop nested inside an x2go sesson, but it should work.  Nested remote desktops do work.

I do use spice from other LAN linux systems into Windows VMs a few times each week. That works well.

---

### Post by rsteinmetz70112 on 2020-12-10
Thanks When I get back to my main office I'll try it.

---


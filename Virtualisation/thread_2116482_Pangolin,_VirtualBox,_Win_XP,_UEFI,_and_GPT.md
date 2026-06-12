---
title: "Pangolin, VirtualBox, Win XP, UEFI, and GPT"
date: 2013-02-15
forum: Virtualisation
---

### Post by acag on 2013-02-15
As I understand it, Windows XP doesn't support UEFI. Ubuntu 12.04 does. I am currently running Ubuntu 12.04 in legacy boot mode and would like to convert to UEFI and GPT. However, I don't want to cause problems for my Windows XP system that is running in a VirtualBox VM under Ubuntu 12.04. Does anyone know whether Ubuntu 12.04 utilizing UEFI and GPT can host a Windows XP system running in VirtualBox?

---

### Post by dcstar on 2013-02-18
> **acag said:**
> As I understand it, Windows XP doesn't support UEFI. Ubuntu 12.04 does. I am currently running Ubuntu 12.04 in legacy boot mode and would like to convert to UEFI and GPT. However, I don't want to cause problems for my Windows XP system that is running in a VirtualBox VM under Ubuntu 12.04. Does anyone know whether Ubuntu 12.04 utilizing UEFI and GPT can host a Windows XP system running in VirtualBox?

VMs run in their own environment, they have nothing whatsoever to do with the boot environment of the host machine.

---

### Post by cscj01 on 2013-03-19
> **dcstar said:**
> VMs run in their own environment, they have nothing whatsoever to do with the boot environment of the host machine.

My understanding of this statement is that I can have Ubuntu boot with UEFI and have an XP VM in Virtualbox boot with Legacy.  Is that correct?

---


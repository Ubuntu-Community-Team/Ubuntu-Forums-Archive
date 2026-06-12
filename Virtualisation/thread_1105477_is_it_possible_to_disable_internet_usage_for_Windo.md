---
title: "is it possible to disable internet usage for Windows XP but allow a VM of Ubuntu?"
date: 2009-03-24
forum: Virtualisation
---

### Post by eival on 2009-03-24
if Windows XP is the main OS and Ubuntu is installed via SunVirtualBox or another VM, could you disable internet usage for windows XP entirely(web browsers, updates, everything...)/ but still allow the VM to have full access the net?

---

### Post by veloce on 2009-03-25
> **eival said:**
> if Windows XP is the main OS and Ubuntu is installed via SunVirtualBox or another VM, could you disable internet usage for windows XP entirely(web browsers, updates, everything...)/ but still allow the VM to have full access the net?

You'd probably need to use windows firewall to do this (shudder).  You'd set up bridged networking for the vm - I think you would need to set the firewall to allow that traffic through and nothing else.

Personally, I'd much rather have the host and vm operating systems around the other way.

---


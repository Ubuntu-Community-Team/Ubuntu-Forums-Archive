---
title: "VMware WindowsXP Remote Desktop"
date: 2009-04-20
forum: Virtualisation
---

### Post by mad_max0204 on 2009-04-20
Hi,

I'm running vmware 6.5 workstation on Ubuntu 8.10 64bit.
Everything updated and working.

Windows XP is installed as guest operating system and networking is set to Bridged. VMware tools are installed and are newest.

My question is this:
How can I access this virtual machine from another computer and what would be the best solution ??
Is vmware's remote display a good solution or should I use windowsxp's remote desktop ? I managed to connect from another ubuntu machine using vmware's remote display but I get a really small desktop and cannot resize it.

Thanks

---

### Post by HermanAB on 2009-04-21
Ensure that the user has a password, then enable RDP and forward port 3389/tcp to the VM.  Rdesktop is a good Linux client for RDP.

---

### Post by mad_max0204 on 2009-04-21
Much appreciated.

---


---
title: "KVM: connect to a guest's VNC with a normal VNC client?"
date: 2008-06-25
forum: Virtualisation
---

### Post by Yann2 on 2008-06-25
Hello, I used to use virt-viewer to connect to the display of my VMs. But i have some colleagues which need access to the VMs as well and who aren't running Hardy yet.
Is it possible to connect to the VM using a normal VNC client? if yes, how?
Thanks!

---

### Post by msisamonopoly on 2008-06-26
On a Windows 2000 VM using Bridge Networking and Static IP I have simply installed VNC Server on the VM and access via vncviewer.

It works fine.

Same principal would apply to a Linux VM - just enable/install VNC Server.

---


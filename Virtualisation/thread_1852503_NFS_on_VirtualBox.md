---
title: "NFS on VirtualBox"
date: 2011-09-30
forum: Virtualisation
---

### Post by yildiz.a on 2011-09-30
Hi,

I have a virtual machine with Ubuntu 11.04 which runs on VirtualBox. However I don't know how to access to folders and files via NFS from a remote machine. Could you help me about this?
Thank you.

---

### Post by pkg9991 on 2011-09-30
what's your host OS
try VMware, it automatically links the host files to the client

---

### Post by yildiz.a on 2011-09-30
> **pkg9991 said:**
> what's your host OS
try VMware, it automatically links the host files to the client

I use Win 7. I need to use VirtualBox.

---

### Post by SeijiSensei on 2011-09-30
By default, VB uses network address translation to connect between the host and guest.  In that configuration, you can't see the guest unless you set up a proxy or use a tunnel.  You probably need to use "bridged networking" as described [here](http://www.virtualbox.org/manual/ch06.html).

---

### Post by yildiz.a on 2011-10-01
> **SeijiSensei said:**
> By default, VB uses network address translation to connect between the host and guest.  In that configuration, you can't see the guest unless you set up a proxy or use a tunnel.  You probably need to use "bridged networking" as described [here](http://www.virtualbox.org/manual/ch06.html).

Thank you.

---


---
title: "Physical 2 Virtual"
date: 2011-01-20
forum: Virtualisation
---

### Post by Santos1204 on 2011-01-20
Dear All,

Does anyone know if it's possible to P2V using KVM/QEMU? I'm trying to move a windows 2003 server over to a virtual machine running under KVM. I know VMware offer this solution but was really hoping it's possible to do it using above. 

Cheers

---

### Post by thomasw_lrd on 2011-01-20
I've tried it in both VMWare and Vbox.  I haven' had much success.  I think if you create a virtual disk large enough, you might be able to just just copy the files directly to it.  I haven't tried this, seeing as I don't have enough disk space.

---

### Post by Santos1204 on 2011-01-21
Thanks for your reply. We use VMware here and physical 2 virtual works really nicely with windows boxes - downside is it costs about £100k :) 

I wanted to do this for a project and couldn't quite fork out the cash, I've heard it's possible but doesn't support windows servers so well....

---

### Post by HermanAB on 2011-01-21
Well, you can run VMware images with the new versions of Virtualbox.  So, you can use the VMware migration tool.

---


---
title: "Access Windows Files"
date: 2008-02-24
forum: Virtualisation
---

### Post by realGaurab on 2008-02-24
I had installed XP with VirtualBox. Now I had problem with the ubuntu install and hence reinstalled ubuntu. However I didn't delete the partition so that I could recover my files. I managed to recover my files from the previous ubuntu install, but have yet to recover from the XP. Can I access the files that I had in virtual XP? I desperately need some files but I don't know where it is located or how to do it. Can somebody please help me.

---

### Post by kpkeerthi on 2008-02-25
VirtualBox virtual disks are usually placed in $HOME/.VirtualBox folder. 

You need to install VirtualBox again and create a VM from "existing" disk by pointing it to $HOME/.VirtualBox folder. Click Add and choose the XP VM you already have. You should be able to boot your virtual XP and copy the files over (after installing vbox guest additions).

Good Luck.

---

### Post by realGaurab on 2008-02-25
Thanks. Let me try it tonight (its early morning right now), I'll post again if I face any problem.

---

### Post by HermanAB on 2008-02-25
A VM is a simply a directory with a bunch of files in it.  You can backup the VM using tar.  In this way, you can copy the VM to another machine or make a copy of the VM.

---


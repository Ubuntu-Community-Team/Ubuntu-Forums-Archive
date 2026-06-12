---
title: "security using a virtual machine running xp"
date: 2008-01-18
forum: Virtualisation
---

### Post by mrbungle on 2008-01-18
i was just wondering if there would be a security problem if i installed virtualbox and put xp on that.  

need to run a couple programs that wine won't do.

---

### Post by bodhi.zazen on 2008-01-18
Security is the same with the guest OS (windows) whether you run it on a computer or VirtualBox.

There is no direct interaction with Windows in Vbox and Ubuntu.

If you enable sharing (hard drive, usb devices, NFS, samba, http, ftp, etc) then security is the same as if you were doing sharing between two phsyical boxes.

---


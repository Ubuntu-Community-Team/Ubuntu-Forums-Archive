---
title: "Cannot start virtualbox"
date: 2009-08-24
forum: Virtualisation
---

### Post by bedlam on 2009-08-24
Have installed the closed virtualbox 3.0 on jaunty but cannot get it to start from the command line. Have tried various options. It tells me, command not found. What must I be doing wrong? Please help

---

### Post by dk06 on 2009-08-24
> **bedlam said:**
> Have installed the closed virtualbox 3.0 on jaunty but cannot get it to start from the command line. Have tried various options. It tells me, command not found. What must I be doing wrong? Please help


Under your user properties, make sure you have VirtualBox as one of your Groups....assign yourself permission to use it.

& make sure the services necessary for VirtualBox to run are running


Hope this helps
___________________
Also, have you agreed to the EULA ? 
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)
[http://www.virtualbox.org/manual/UserManual.html](http://www.virtualbox.org/manual/UserManual.html)

---

### Post by slakkie on 2009-08-24
Check if you are in the vbox group.

id or groups command will help you in finding out.

---

### Post by bedlam on 2009-08-24
> **bedlam said:**
> Have installed the closed virtualbox 3.0 on jaunty but cannot get it to start from the command line. Have tried various options. It tells me, command not found. What must I be doing wrong? Please help
Have actually found the answer by reading the docs found in /./usr/share/doc/virtualbox-3.0/. Very interesting, Thanks anyway for your help

---


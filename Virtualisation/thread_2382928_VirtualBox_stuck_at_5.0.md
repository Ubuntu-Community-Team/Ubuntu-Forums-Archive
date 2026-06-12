---
title: "VirtualBox stuck at 5.0"
date: 2018-01-18
forum: Virtualisation
---

### Post by spookey2 on 2018-01-18
> **DuckHook said:**
> I experienced exactly the same problem. The problem is VB 5.0. You need to update to VB 5.2.

[LIST=1]
[*]Uninstall VB completely (Your VMs should be safe. They aren't touched by an uninstall. But make sure you are backed up as a matter of policy.).
[*]If not already present, add the Oracle PPA: [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian)
[*]Then:```
sudo apt update
```
[*]Open Software Centre and install VB 5.2
[/LIST]


That didn't work at all, it still pulls VB 5.0.

---

### Post by DuckHook on 2018-01-18
Your post has been moved to its own thread in Virtualisation with a new title that is more relevant to your issue. Also, just a friendly reminder not to hijack threads.

Please appreciate that you've given us absolutely nothing to go on. What steps did you take? How did you add the PPA? If added properly, did you do a:```
sudo apt update
```…before looking in Software Centre?

---

### Post by deadflowr on 2018-01-19
You need to actually install virtualbox-5.2
That's the package name.

---

### Post by SeijiSensei on 2018-01-20
The procedure described at 

[https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

always works for me.

---


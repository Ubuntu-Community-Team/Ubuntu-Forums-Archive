---
title: "Ubuntu 12.04 64bit stuck at installing vmware tools"
date: 2012-06-06
forum: Virtualisation
---

### Post by makrand on 2012-06-06
I am new to linux and vmware. I wanted to install Ubuntu 12.04 64 bit on VMware Workstation 8. the install seemed to be fine, but when i checked back, then it was stuck on the following screen:
[IMG]http://i47.tinypic.com/13yp8xd.png[/IMG]
(also attached)

I also tried restarting the virtual machine, but still it begins installing vmware tools and gets stuck there

Can someone tell me whats wrong or if i am missing something or doing it wrong?

---

### Post by 1728 on 2012-06-06
Do you need vmware specifically? If not, virtualbox is in the software center and usually installs without an issue.

---

### Post by dcstar on 2012-06-07
> **makrand said:**
> 
...........
Can someone tell me whats wrong or if i am missing something or doing it wrong?

**Do not** use the "Easy Install" option, VMware does not fully support 12.04  yet.

Use the Manual Install option and point the CD to the ISO image.

---

### Post by afz on 2012-09-12
I had the same problem but I resolved it.
While creating a new virtual machine, you're asked how will you install the Guest OS and there are three options
1- Installer disc:
2- Installer disc image file (iso):
3- I will install the operating system later.

The problem rose when I selected the 2nd option and browsed to the Ubuntu iso image file. The next time I selected the 3rd option and the problem was gone.

Hope it helps.

---

### Post by Welly Wu on 2012-09-12
You need to upgrade to VM Ware Workstation 9.x 32 or 64 bit. It fully supports Ubuntu 12.04.x LTS 32 and 64 bit as a guest virtual machine with OpenGL 2.1 3D hardware graphics acceleration. You can also use it with Ubuntu 12.04.x 32 and 64 bit Long Term Service as the host operating system like I do.

---


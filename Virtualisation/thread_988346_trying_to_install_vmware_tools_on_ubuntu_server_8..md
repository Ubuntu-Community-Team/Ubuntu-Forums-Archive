---
title: "trying to install vmware tools on ubuntu server 8.04"
date: 2008-11-20
forum: Virtualisation
---

### Post by drtanz on 2008-11-20
hi i am quite new to ubuntu, but basically what i want to do is install vmware tools on my ubuntu server. I am using vmware of course, so i clicked on vm>install vmware tools and then checked the contents of cdrom0 and the files seem to be those for the windows version of vmware tools. is this normal or is this the wrong version of vmware tools being loaded to my system? how can i fix it?

---

### Post by fjgaude on 2008-11-20
Your server is running Ubuntu, your have VMware server, with Windows as your VM? If so, then the tools are for Windows; they make the mouse and video work as they should.

---

### Post by drtanz on 2008-11-20
No I have win xp installed as my main OS, and im using vmware workstation to run ubuntu server as the vm.

---

### Post by bodhi.zazen on 2008-11-20
[https://help.ubuntu.com/community/VMware/Tools](https://help.ubuntu.com/community/VMware/Tools)

---

### Post by drtanz on 2008-11-20
problem is i cannot find the VMwareTools*.tar.gz on the mounted cd, there are only windows files visible in the file browser.

---

### Post by drtanz on 2008-11-21
any further help on this? thanks

---

### Post by bodhi.zazen on 2008-11-21
Did you mount the iso (typically in /media/cdrom) ?

What is in the directory ?

```
ls /media/cdrom
```I looked at this last night and the files were there ??? You do understand that the "*" is a variable.

---

### Post by drtanz on 2008-11-21
ok found out the problem, the virtual machine was set as being windows thus the incorrect version of vmware tools was being loaded. thanks

---


---
title: "cannot run guest additions in virtual box"
date: 2009-05-14
forum: Virtualisation
---

### Post by fonseca44 on 2009-05-14
I have tried continuously to run guest additions in virtual box but cannot. 
I have opened guess additions up and executed it from the cd image but receive an error message when it begans to run stating that the program must be run with administrator priviledges. I have administrator priviledges or at least i thought. I should be a super user. when i open up the terminal and run it states it cant open media/cdrom/vboxlinuxadditions.run. I have copy the files to my home folder and tried to open the additions from there with no luck.

---

### Post by bluefrog on 2009-05-14
you must run the additions in the guest

---

### Post by bodhi.zazen on 2009-05-14
Depending on the guest OS, run the installer as root (either su - or sudo -i then run the installer or  sudo /path/to/install_script).

---


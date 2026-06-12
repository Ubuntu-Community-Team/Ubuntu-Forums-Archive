---
title: "Howto: running Ubuntu Snappy in VirtualBox"
date: 2015-01-09
forum: Virtualisation
---

### Post by sanderj on 2015-01-09
FYI: a how-to run Ubuntu Snappy in Virtualbox:

```
wget http://cdimage.ubuntu.com/ubuntu-core/preview/ubuntu-core-alpha-01.img
qemu-img convert -O vdi ubuntu-core-alpha-01.img ubuntu-core-alpha-01.vdi
```

You should now have two files:
```
-rw-rw-r--   1 sander sander 1618149376 jan  2 20:17 ubuntu-core-alpha-01.img
-rw-r--r--   1 sander sander 1592869376 jan 10 00:47 ubuntu-core-alpha-01.vdi
```


Now start Virtualbox, create a new virtual machine, follow the usual steps, BUT in the step "Create Virtual Machine - Hard Drive" (where you normally create a new virtual hard disk), choose "Choose an Existing Virtual Hard Drive File" and pick the file ubuntu-core-alpha-01.vdi you just created.
Proceed in create steps. Then start your new virtual machine running Ubuntu Snappy. Login is ubuntu/ubuntu.


Easy, isn't it?

---

### Post by rafaellcustodio on 2015-01-26
Hi, I made this with alpha-02 and........it works :)

Are there a way to set the resolution to 1024x768??

---

### Post by john360 on 2015-02-08
Hi there, tried this with latest ubuntu qemu. When I try to use the vdi I get invalid format message from vbox.  Any ideas? 

Can you show the commands you used. TIA 
John

---

### Post by john360 on 2015-02-08
Thanks, this works but is very slow so can't do update. 

Any ideas [lease? 

Would alpha-02 be faster? How can I get it and use in vb?

TIA John

---


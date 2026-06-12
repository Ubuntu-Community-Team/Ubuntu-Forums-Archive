---
title: "VMware and Ubuntu Hardy prob"
date: 2008-08-25
forum: Virtualisation
---

### Post by NetSkay on 2008-08-25
hey guys im trying to install vmware tools on a guest OS but i have prob with the C header files... apperently they dont match my running kernel... any ideas?!
i did 
sudo apt-get install linux source
sudo apt-get install linux-headers

which dir should i point the installer at?!

---

### Post by erwall on 2008-08-25
> **NetSkay said:**
> hey guys im trying to install vmware tools on a guest OS but i have prob with the C header files... apperently they dont match my running kernel... any ideas?!
i did 
sudo apt-get install linux source
sudo apt-get install linux-headers

which dir should i point the installer at?!
have you tried
```
uname -r
```
and putting the output in place of 'uname -r'?
```
sudo aptitude install linux-headers-'uname -r'
```

---

### Post by NetSkay on 2008-08-30
okay i did this and i have everything and i get this message, same as before...

What is the location of the directory of C header files that match your running kernel? [/usr/src/linux/incclude]
i put this
/usr/src/linux-headers-2.6.24-19-generic/include

installer response
the directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match your running kernel (version 2.6.24-19-generic). even if the module were to compile successfully, it would not load into the running kernel

then it asks for the directory again wtf?!

---

### Post by overdrank on 2008-08-30
Moved to Virtualization. :)
Hi and welcome you may look at the sticky in this forum
[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

---


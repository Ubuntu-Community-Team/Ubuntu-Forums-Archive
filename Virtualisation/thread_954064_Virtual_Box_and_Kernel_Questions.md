---
title: "Virtual Box and Kernel Questions"
date: 2008-10-20
forum: Virtualisation
---

### Post by crimsongrim on 2008-10-20
My first question is what is the difference between the kernels: 2.6.24-17-generic and 2.6.24-21-generic?

My second question is why when i use 2.6.24-21-generic virtual box will not work ? I had first installed Virtual Box on 2.6.24-17-generic and it was PUEL version and worked fine, now that i tried to use Virtual Box on the latest Kernel(2.6.24-21-generic) it won't work either, you can see the error message that i attached.

Hope same one can help with this?

---

### Post by tuxxy on 2008-10-20
Run the following command in terminal should fix it

```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by crimsongrim on 2008-10-20
Ok
so if i run the code on 2.6.24-17-generic it should fix it?
and if i run it in 2.6.24-21 will i be able to run it there?

---

### Post by tuxxy on 2008-10-20
Run the code in the new kernel if thats where you are having the problems

---

### Post by crimsongrim on 2008-10-20
i was using Virtual box in 2.6.24-17 first so i guess i will do it there.
But if I want to use it in the new kernels will i have to re-install?

---

### Post by cicatrix1 on 2008-10-20
> **crimsongrim said:**
> i was using Virtual box in 2.6.24-17 first so i guess i will do it there.
But if I want to use it in the new kernels will i have to re-install?

VirtualBox has a kernel module that must be recompiled when you start using a different kernel.  The initial VirtualBox install compiles the module by default, but now that you have upgraded you must run the mentioned command in order to build the module for your new kernel.

Just boot into the new kernel and run the command.  I'm not 100%, but you may or may not have to reboot after you do that.  You shouldn't have to reinstall anything.  VirtualBox just needs to hook into the kernel via it's module, so after you rebuild it for the new kernel you'll be just fine :)

---

### Post by tuxxy on 2008-10-20
Run the command for any kernel that returns you the error also reboot shouldnt be necessary

---

### Post by crimsongrim on 2008-10-20
THANKS!!
I'll try it and hope it works!

---


---
title: "VirtualBox Error (Gutsy version on 10.04)"
date: 2011-06-21
forum: Virtualisation
---

### Post by jim78 on 2011-06-21
I've just installed VirtualBox and am getting this error:

> VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root. VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED)

I've done as it said in the message and nothing happens. Has anyone got any suggestions? I really need to run xp for some work I have to do.

---

### Post by Dedoimedo on 2011-06-21
Did you execute the command as sudo?
If you type /sbin/lsmod|grep vbox - what do you see?
If you run sudo /etc/init.d/vboxdrv start, what happens?
Dedoimedo

---

### Post by jim78 on 2011-06-21
Hi, yes I ran it as sudo. The grep command gives me nothing, just goes back to the command prompt and the start command gives me:

> * Starting VirtualBox kernel module                                            
 * No suitable module for running kernel found


---

### Post by Jake.Debord on 2011-06-21
You may need to start again with a fresh vboxdrv file, it's possible that one is corrupt in some way...

---

### Post by Dedoimedo on 2011-06-22
> **jim78 said:**
> Hi, yes I ran it as sudo. The grep command gives me nothing, just goes back to the command prompt and the start command gives me:

What about the other commands.
Can you please run and post output?
Dedoimedo

---

### Post by slooksterpsv on 2011-06-22
Try the Lucid Lynx version; there may be differences between GG and LL for it not to work.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---


---
title: "VMWare server 1.09/64-bit jaunty? Retreat looming"
date: 2009-05-30
forum: Virtualisation
---

### Post by lenticular on 2009-05-30
Hi-

I have 4 PCs set with Hardy and VMWare Server 1.08.  It has been very handy to be able to stamp out VMs on my desktop, then transfer them to the three laptops.

Today,for a lark, I installed jaunty 64-bit on my desktop, but was unable to get VMWare 1.09 to compile:

/tmp/vmware-config0/vmmon-only/linux/driver.c:1670: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

I did install VMWare server 2.0, but the Web interface doesn't cut it for me and I don't want to have to upgrade my three laptops to 2.0.  I've looked around the web to debug my 1.09 compile problem without much luck.  At this point, I'm thinking I'll just fall back to 32-bit Hardy on my desktop, but I wondered if anyone had any pointers that might save me the trouble?

Thanks,
 John

---

### Post by dcstar on 2009-05-31
> **lenticular said:**
> Hi-

I have 4 PCs set with Hardy and VMWare Server 1.08.  It has been very handy to be able to stamp out VMs on my desktop, then transfer them to the three laptops.

Today,for a lark, I installed jaunty 64-bit on my desktop, but was unable to get VMWare 1.09 to compile:

/tmp/vmware-config0/vmmon-only/linux/driver.c:1670: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

I did install VMWare server 2.0, but the Web interface doesn't cut it for me and I don't want to have to upgrade my three laptops to 2.0.  I've looked around the web to debug my 1.09 compile problem without much luck.  At this point, I'm thinking I'll just fall back to 32-bit Hardy on my desktop, but I wondered if anyone had any pointers that might save me the trouble?

Thanks,
 John

There are numerous posts on installing 64-bit VMWare 1.0.x, just find one and follow the instructions.

---

### Post by lenticular on 2009-05-31
Yep, search is a wonderful thing.  For sure.  That's why I used it before posting.  The main threads suggest the any-any patch, but I just get no joy.  For instance, following the steps suggested here:
[http://ubuntuforums.org/showthread.php?t=826624&highlight=64-bit+vmware+server](http://ubuntuforums.org/showthread.php?t=826624&highlight=64-bit+vmware+server) gives me the same error.

All packages needed are installed and current.

Perhaps, David, I could trouble you to point me to some of those numerous threads you mentioned.

Thanks,
  John

---

### Post by dcstar on 2009-05-31
> **lenticular said:**
> Yep, search is a wonderful thing.  For sure.  That's why I used it before posting.  The main threads suggest the any-any patch, but I just get no joy.  For instance, following the steps suggested here:
[http://ubuntuforums.org/showthread.php?t=826624&highlight=64-bit+vmware+server](http://ubuntuforums.org/showthread.php?t=826624&highlight=64-bit+vmware+server) gives me the same error.

All packages needed are installed and current.

Perhaps, David, I could trouble you to point me to some of those numerous threads you mentioned.



[http://ubuntuforums.org/showthread.php?t=966070](http://ubuntuforums.org/showthread.php?t=966070)
[http://ubuntuforums.org/showthread.php?t=1120414](http://ubuntuforums.org/showthread.php?t=1120414)

Download the VMWare 1.09 server .gz file, download and install the patch file and following the successful completion of all instructions, run this code to fix things on 64-bit systems so the console will run:

```
sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1
sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0
sudo ln -s /usr/lib32 /usr/l32
sudo sed -i -e 's:usr/lib/:usr/l32/:g'  /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
sudo sed -i -e 's:usr/lib/:usr/l32/:g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.9
```

---

### Post by lenticular on 2009-05-31
That was extremely helpful, David!  I'm up and running now.

Thanks so much for your help.

-John

---

### Post by bodhi.zazen on 2009-05-31
Thank you dcstar for linking to the threads I make re: VMWare. It is helpful to see them used and it helps me keep them up to date ;)

---

### Post by lenticular on 2009-05-31
Thank you as well, Bodhi.  Very nice guides!

-John

---


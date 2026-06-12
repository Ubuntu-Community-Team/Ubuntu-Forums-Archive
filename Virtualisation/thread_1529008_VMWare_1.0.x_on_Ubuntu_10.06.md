---
title: "VMWare 1.0.x on Ubuntu 10.06"
date: 2010-07-11
forum: Virtualisation
---

### Post by epp_b on 2010-07-11
I've managed to install VMWare 2.0.2 using [these instructions](http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/), but the stupid WebAccess system blows huge whale blubber chunks.

I've since uninstalled 2.0 and tried to install 1.0.10 and have found nothing that works.

Here are the errors at the end of the build attempt:

```

make[2]: *** [/tmp/vmware-config7/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config7/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-23-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config7/vmmon-only'
Unable to build the vmmon module.

Execution aborted.

```

I really don't want to spend a day dicking around with the kernel (as described [here](http://www.howtoforge.com/how-to-install-vmware-server-1.0.x-on-a-kubuntu-10.04-desktop)), what can I do to get this working?

---

### Post by fjgaude on 2010-07-11
The best approach is to use VMware Player 3.1.0... it works with all later versions of Ubuntu.

---

### Post by epp_b on 2010-07-11
Thanks, that seems to work alright.  I still prefer the old VMware Server, as I can connect remotely from a console on another machine.

Nevertheless, the computer on which I'm attempted to run VMware is pretty old.  I've decided to forgo VMware and just install the OS on metal.

---

### Post by roxette on 2010-07-15
same question

how to install vmware server 1.0 on ubuntu 10.04 server?
some files are different between ubuntu 8.04 and 10.04

---


---
title: "VM Ware install question"
date: 2009-03-23
forum: Server Platforms
---

### Post by BradleyAtkins on 2009-03-23
Hi all

I have just downloaded VMWare Server and want to install it on a server I have just bought running Ubuntu Server 8.10.

Looking in the installation instructions I don't know how check if the following applies: -

**Installing VMware Server on a Linux Host**
Before you begin, read the following notes and make adjustments to your host system: -
&#56256;&#56452; The real&#8208;time clock function must be compiled in your Linux kernel.
&#56256;&#56452; The parallel port PC&#8208;style hardware option (CONFIG_PARPORT_PC) must be built and loaded as a kernel module (that is, it must be set to m when the kernel is compiled).

How do I find out if the kernel was compiled in this fashion and if not how do I go about compiling it?

Many thanks

Bradley

---

### Post by Bachstelze on 2009-03-23
```
firas@iori ~ % grep CONFIG_PARPORT_PC /boot/config-`uname -r`
CONFIG_PARPORT_PC=m

```

---

### Post by BradleyAtkins on 2009-03-23
Hi Hymself

Thanks

root@poweredge:~# grep CONFIG_PARPORT_PC /boot/config-`uname -r`
CONFIG_PARPORT_PC=m
CONFIG_PARPORT_PC_FIFO=y
CONFIG_PARPORT_PC_PCMCIA=m
# CONFIG_PARPORT_PC_SUPERIO is not set

Any ideas on the real time clock function?

Many thanks

---


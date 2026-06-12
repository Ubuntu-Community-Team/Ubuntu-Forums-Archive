---
title: "vmware installation in hardy"
date: 2008-05-07
forum: Server Platforms
---

### Post by cacharreo on 2008-05-07
I cannot install VmWare Server 1.0.5 in Hardy. I get problems with vmmon module while compiling, see the following terminal messages:

[B][I]Building the vmmon module.

Using 2.6.x kernel build system.
make: se ingresa al directorio `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.24-17-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.24-17-386'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:48:
/tmp/vmware-config0/vmmon-only/./include/vm_basic_types.h:161: error: tipos en conflicto para ‘uintptr_t’
include/linux/types.h:40: error: la declaración previa de ‘uintptr_t’ estaba aquí
En el fichero incluído de /tmp/vmware-config0/vmmon-only/linux/driver.h:20,
                 de /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:37:5: aviso: "VMW_HAVE_EPOLL" no está definido
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:43:5: aviso: "VMW_HAVE_EPOLL" no está definido
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:60: error: tipos en conflicto para ‘poll_initwait’
include/linux/poll.h:65: error: la declaración previa de ‘poll_initwait’ estaba aquí
/tmp/vmware-config0/vmmon-only/linux/driver.c:147: aviso: inicialización desde un tipo de puntero incompatible
/tmp/vmware-config0/vmmon-only/linux/driver.c:151: aviso: inicialización desde un tipo de puntero incompatible
/tmp/vmware-config0/vmmon-only/linux/driver.c: En la función ‘LinuxDriver_Ioctl’:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1659: error: ‘struct mm_struct’ no tiene un miembro llamado ‘dumpable’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.24-17-386'
make: *** [vmmon.ko] Error 2
make: se sale del directorio `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

[/I][/B]

Some idea ????
Thank you

---

### Post by quelx on 2008-05-08
You probably need to check out the vmware-update-any-any package: [http://howtoforge.com/vmware-server-on-ubuntu8.04](http://howtoforge.com/vmware-server-on-ubuntu8.04)

I needed it to install 1.0.5 on Hardy

---

### Post by bapoumba on 2008-05-08
May be look [here]("http://ubuntuforums.org/showthread.php?p=4868919") too :)

---

### Post by K.Morgan on 2008-05-08
This is something i would like to know also.  All the links that i have found so far including the ones above are for those upgrading, or already had vmware installed on Ubuntu 7.10 and had it stop working in 8.04.

I need to install vmware from scratch on Ubuntu 8.04

Kristian

---

### Post by cacharreo on 2008-05-08
thank you quelx it works:guitar:

---

### Post by chinaski on 2008-05-08
> **bapoumba said:**
> May be look [here]("http://http://ubuntuforums.org/showthread.php?p=4868919") too :)
link is wrong, double http ;)

---

### Post by K.Morgan on 2008-05-09
> **chinaski said:**
> link is wrong, double http ;)

Thanks that did it.

Kristian

---

### Post by opus on 2008-05-09
Here is another guide.  The guy who wrote this one is an Ubuntu Guru.

[http://ubuntu-tutorials.com/2008/05/03/install-vmware-server-105-on-ubuntu-804-hardy/]("http://ubuntu-tutorials.com/2008/05/03/install-vmware-server-105-on-ubuntu-804-hardy/")

Aaron Throckmorton
[Admin Daily - Daily Systems Administration]("http://admindaily.blogspot.com/")

---


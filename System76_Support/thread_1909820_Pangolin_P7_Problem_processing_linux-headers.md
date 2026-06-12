---
title: "Pangolin P7 Problem processing linux-headers"
date: 2012-01-16
forum: System76 Support
---

### Post by AmadeusOK on 2012-01-16
I'm running Ubuntu 10.04 on my laptop. When I tried to install some software I got this error message:

```
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-32-generic'
  CC [M]  /opt/system76/system76-driver/src/jme-1.0.5/jme.o
/opt/system76/system76-driver/src/jme-1.0.5/jme.c: In function ‘jme_set_multi’:
/opt/system76/system76-driver/src/jme-1.0.5/jme.c:2060: error: ‘struct net_device’ has no member named ‘mc_list’
/opt/system76/system76-driver/src/jme-1.0.5/jme.c:2061: error: ‘struct net_device’ has no member named ‘mc_count’
/opt/system76/system76-driver/src/jme-1.0.5/jme.c:2062: error: dereferencing pointer to incomplete type
/opt/system76/system76-driver/src/jme-1.0.5/jme.c:2064: error: dereferencing pointer to incomplete type
make[2]: *** [/opt/system76/system76-driver/src/jme-1.0.5/jme.o] Error 1
make[1]: *** [_module_/opt/system76/system76-driver/src/jme-1.0.5] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-32-generic'
make: *** [all] Error 2
make: Leaving directory `/opt/system76/system76-driver/src/jme-1.0.5'
run-parts: /etc/kernel/header_postinst.d/jme exited with return code 2
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.35-30-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.35-30-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-headers-2.6.35-31-generic (2.6.35-31.63) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
 * dkms: running auto installation service for kernel 2.6.35-31-generic                                                                                                                               
 *       fglrx (8.780)...                                                                                                                                                                      [ OK ] 
run-parts: executing /etc/kernel/header_postinst.d/jme 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
make: Entering directory `/opt/system76/system76-driver/src/jme-1.0.5'
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-32-generic'
  CC [M]  /opt/system76/system76-driver/src/jme-1.0.5/jme.o
/opt/system76/system76-driver/src/jme-1.0.5/jme.c: In function ‘jme_set_multi’:
/opt/system76/system76-driver/src/jme-1.0.5/jme.c:2060: error: ‘struct net_device’ has no member named ‘mc_list’
/opt/system76/system76-driver/src/jme-1.0.5/jme.c:2061: error: ‘struct net_device’ has no member named ‘mc_count’
/opt/system76/system76-driver/src/jme-1.0.5/jme.c:2062: error: dereferencing pointer to incomplete type
/opt/system76/system76-driver/src/jme-1.0.5/jme.c:2064: error: dereferencing pointer to incomplete type
make[2]: *** [/opt/system76/system76-driver/src/jme-1.0.5/jme.o] Error 1
make[1]: *** [_module_/opt/system76/system76-driver/src/jme-1.0.5] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-32-generic'
make: *** [all] Error 2
make: Leaving directory `/opt/system76/system76-driver/src/jme-1.0.5'
run-parts: /etc/kernel/header_postinst.d/jme exited with return code 2
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.35-31-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.35-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-headers-2.6.35-32-generic (2.6.35-32.64) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.35-32-generic /boot/vmlinuz-2.6.35-32-generic
 * dkms: running auto installation service for kernel 2.6.35-32-generic                                                                                                                               
 *       fglrx (8.780)...                                                                                                                                                                      [ OK ] 
run-parts: executing /etc/kernel/header_postinst.d/jme 2.6.35-32-generic /boot/vmlinuz-2.6.35-32-generic
make: Entering directory `/opt/system76/system76-driver/src/jme-1.0.5'
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-32-generic'
  CC [M]  /opt/system76/system76-driver/src/jme-1.0.5/jme.o
/opt/system76/system76-driver/src/jme-1.0.5/jme.c: In function ‘jme_set_multi’:
/opt/system76/system76-driver/src/jme-1.0.5/jme.c:2060: error: ‘struct net_device’ has no member named ‘mc_list’
/opt/system76/system76-driver/src/jme-1.0.5/jme.c:2061: error: ‘struct net_device’ has no member named ‘mc_count’
/opt/system76/system76-driver/src/jme-1.0.5/jme.c:2062: error: dereferencing pointer to incomplete type
/opt/system76/system76-driver/src/jme-1.0.5/jme.c:2064: error: dereferencing pointer to incomplete type
make[2]: *** [/opt/system76/system76-driver/src/jme-1.0.5/jme.o] Error 1
make[1]: *** [_module_/opt/system76/system76-driver/src/jme-1.0.5] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-32-generic'
make: *** [all] Error 2
make: Leaving directory `/opt/system76/system76-driver/src/jme-1.0.5'
run-parts: /etc/kernel/header_postinst.d/jme exited with return code 2
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.35-32-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.35-32-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.35-32-generic; however:
  Package linux-headers-2.6.35-32-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
Setting up testdisk (6.11-1) ...
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-headers-2.6.35-30-generic
 linux-headers-2.6.35-31-generic
 linux-headers-2.6.35-32-generic
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

What could be the problem? Thanks in advance.

---

### Post by smarmytime on 2012-01-16
What is the software you were trying to install, and were you installing it, or compiling it?

---

### Post by isantop on 2012-01-17
Why do you have 2.6.35 installed on 10.04? The recommended kernel for 10.04 was 2.6.32, and I'd recommend staying there. 

If you didn't upgrade the kernel manually, then there's a chance that upgrading to a more recent version of Ubuntu will solve the problem.

---

### Post by AmadeusOK on 2012-01-17
> **smarmytime said:**
> What is the software you were trying to install, and were you installing it, or compiling it?

Most of the time when I try to install new software I get some kind of error message. I was trying to install from source gtypist, PARI-GP, and PhotoRec. But also when I use Synaptic and even when I try to update the system using the Update Manager I get this error messages.

---

### Post by AmadeusOK on 2012-01-17
> **isantop said:**
> Why do you have 2.6.35 installed on 10.04? The recommended kernel for 10.04 was 2.6.32, and I'd recommend staying there. 

If you didn't upgrade the kernel manually, then there's a chance that upgrading to a more recent version of Ubuntu will solve the problem.

That could be the reason. The only thing I did long ago was to update the system and the 2.6.35 kernel got installed. I tried to upgrade to Ubuntu 11.04 but the process aborted with an error message.

---

### Post by isantop on 2012-01-18
This is telling me that you may need to perform a reinstallation. This will get you a fresh set of software and fix any issue left behind from your failed upgrade. We recommend installing Ubuntu 11.10.

---


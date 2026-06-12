---
title: "Upgrade Lumur Laptop to 10.10"
date: 2010-10-19
forum: System76 Support
---

### Post by rokstar on 2010-10-19
At the end of the upgrade process to 10.10 on my Lemur laptop I have the following problem. When dpkg runs to finish installing the linux kernel 2.6.35-22 it fails.

Here's the end of the log message of the update manager.

Errors were encountered while processing:

 linux-headers-2.6.35-22-generic

Setting up linux-headers-2.6.35-22-generic (2.6.35-22.34) ...

Examining /etc/kernel/header_postinst.d.

run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic

 * dkms: running auto installation service for kernel 2.6.35-22-generic        

 *       virtualbox-ose (3.2.8)...        
[ OK ]

run-parts: executing /etc/kernel/header_postinst.d/jme 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic

make: Entering directory `/opt/system76/system76-driver/src/jme-1.0.5'

make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'

  CC [M]  /opt/system76/system76-driver/src/jme-1.0.5/jme.o

/opt/system76/system76-driver/src/jme-1.0.5/jme.c: In function ‘jme_set_multi’:

/opt/system76/system76-driver/src/jme-1.0.5/jme.c:2060: error: ‘struct net_device’ has no member named ‘mc_list’

/opt/system76/system76-driver/src/jme-1.0.5/jme.c:2061: error: ‘struct net_device’ has no member named ‘mc_count’

/opt/system76/system76-driver/src/jme-1.0.5/jme.c:2062: error: dereferencing pointer to incomplete type

/opt/system76/system76-driver/src/jme-1.0.5/jme.c:2064: error: dereferencing pointer to incomplete type

make[2]: *** [/opt/system76/system76-driver/src/jme-1.0.5/jme.o] Error 1

make[1]: *** [_module_/opt/system76/system76-driver/src/jme-1.0.5] Error 2

make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'

make: *** [all] Error 2

make: Leaving directory `/opt/system76/system76-driver/src/jme-1.0.5'

run-parts: /etc/kernel/header_postinst.d/jme exited with return code 2

Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.35-22-generic.postinst line 110.

dpkg: error processing linux-headers-2.6.35-22-generic (--configure):

 subprocess installed post-installation script returned error exit status 2



Anyone have any suggestions?  Thanks for your help!

---

### Post by isantop on 2010-10-20
Try opening a terminal (Applications > Accessories > Terminal) and running:
```
sudo apt-get remove --purge -y system76-driver
```

This will remove the System76 Driver, which I believe is causing the problem. You can reinstall it after the upgrade is complete.

---

### Post by cyrus0101 on 2010-10-21
I've got the same problem. I purged the system 76 driver, but the error remains the same.

---

### Post by rokstar on 2010-10-21
I tried that as well and it didn't work for me.  Anyone have any other ideas?

---

### Post by isantop on 2010-10-22
cyrus0101: Could you open a terminal and send me the output of:

```
ls -a /opt
```


rokstar: Are you getting the same errors listed in the first post? If so, please follow the direction above for cyrus0101. If not, you may want to open a new thread.

---

### Post by cyrus0101 on 2010-10-22
> **isantop said:**
> cyrus0101: Could you open a terminal and send me the output of:

```
ls -a /opt
```


rokstar: Are you getting the same errors listed in the first post? If so, please follow the direction above for cyrus0101. If not, you may want to open a new thread.

Right on, thanks for the help:

```

cyrus@albatross:/opt$ ls -la
total 20
drwxr-xr-x  5 root root 4096 2010-10-22 17:28 .
drwxr-xr-x 22 root root 4096 2010-10-22 17:27 ..
drwxr-xr-x  4 root root 4096 2010-09-02 19:51 google
drwxr-xr-x  3 root root 4096 2010-04-17 21:51 java
drwxr-xr-x  3 root root 4096 2010-02-23 20:03 system76

```

---

### Post by isantop on 2010-10-22
Okay, I thought that would be the case. Try running:
```
sudo rm -rv /opt/system76
```
Post the output here, and then try the upgrade again.

---

### Post by cyrus0101 on 2010-10-23
Unfortunately, that didn't work. Somewhere, this source is being linked in to the reconfigure process. Removing the source just seems to change the error from a broken compile to a missing file:

Thanks again for all the help...

```

cyrus@albatross:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up linux-headers-2.6.35-22-generic (2.6.35-22.35) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
 * dkms: running auto installation service for kernel 2.6.35-22-generic                                                                                                                           
 *       vboxhost (3.2.10)...                                                                                                                                                              [ OK ] 
run-parts: executing /etc/kernel/header_postinst.d/jme 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
python: can't open file '/opt/system76/system76-driver/src/jme_kernel_update.py': [Errno 2] No such file or directory
make: *** /opt/system76/system76-driver/src/jme-1.0.5/: No such file or directory.  Stop.
run-parts: /etc/kernel/header_postinst.d/jme exited with return code 2
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.35-22-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.35-22-generic; however:
  Package linux-headers-2.6.35-22-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 linux-headers-2.6.35-22-generic
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by rokstar on 2010-10-23
I had the same results.  Thanks for offering your help everyone! I hope we can resolve this soon.

---

### Post by rokstar on 2010-10-23
I did some searching around the net and found that there was a similar error with a broadcom device.  I'm wondering if it might be time to file a bug report because the issue seems to be related to the driver source.

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/590924](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/590924)

What do you guys think?

But everything seems to be working fine, maybe we just need to figure out how to unlink this driver?

---

### Post by vkurup on 2010-11-17
I had the same error and was able to fix it by:

1) Purging the system76-driver
2) Deleting the file /etc/kernel/header_postinst.d/jme (actually just mv'ing it)
3) sudo aptitude install (to properly configure the linux-headers pkg)
4) sudo aptitude install system76-driver

This seemed to work, but then again, my system doesn't require any custom drivers from System76 (pangolin), so YMMV.

---


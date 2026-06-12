---
title: "boot_cpu_data virtualbox installation problem"
date: 2007-11-13
forum: Virtualisation
---

### Post by strikenowhere on 2007-11-13
Hello,

I am currently trying to perform an installation of VirtualBox on an Ubuntu Linux 6.06 2.6.15-26-server. However, I am running into an error when running /etc/init.d/vboxdrv setup. I constantly get this error message:

```


root@mars:~# /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module vboxdrv                             [ ok ]
 * Recompiling VirtualBox kernel module vboxdrv                          [ ok ]
 * Starting VirtualBox kernel module vboxdrv                                    FATAL: Error inserting vboxdrv (/lib/modules/2.6.15-26-server/misc/vboxdrv.ko): Unknown symbol in module, or unknown parameter (see dmesg)

 * Modprobe vboxdrv failed. Please use 'dmesg' to find out why.


```

When I check dmesg, this message appears:

```


[43034687.020000] vboxdrv: disagrees about version of symbol boot_cpu_data
[43034687.020000] vboxdrv: Unknown symbol boot_cpu_data


```

Does anyone know what the deal is with this error? I am using linux-source-2.6.15  and I performed the "make oldconfig" and "make vmlinux" on it, along with setting the "export KERN_DIR=/usr/src/linux-source-2.6.15".

Any help would be appreciated!

Greg

---


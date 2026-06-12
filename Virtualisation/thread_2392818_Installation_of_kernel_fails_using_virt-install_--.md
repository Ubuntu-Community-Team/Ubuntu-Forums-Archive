---
title: "Installation of kernel fails using virt-install --location"
date: 2018-05-25
forum: Virtualisation
---

### Post by Tuna-Fish on 2018-05-25
I am trying to install ubuntu on a virtual machine like this:
```

virt-install --name myhostname --ram 512 --disk /home/myusername/myhostname.img,bus=virtio,format=raw,driver_type=raw --arch x86_64 --network bridge=br0 --location http://mirrors.nic.funet.fi/ubuntu/dists/bionic/main/installer-amd64 --graphics none --extra-args='console=ttyS0,115200n8 serial'

```

The installer runs smoothly right up to the point where it's supposed to install the kernel, and then dies with the rather mystic error message of:
> 
 Unable to install the selected kernel An error was returned while trying to install the kernel into the target system.


With a helpful message to look into /var/log/syslog for details, only for it to have the less than helpful:
> 
May 25 21:00:44 in-target: Setting up linux-headers-generic (4.15.0.22.23) ...
May 25 21:00:44 in-target: ^M
May 25 21:00:45 base-installer: error: exiting on error base-installer/kernel/failed-install
May 25 21:00:54 main-menu[275]: WARNING **: Configuring 'bootstrap-base' failed with error code 1
May 25 21:00:54 main-menu[275]: WARNING **: Menu item 'bootstrap-base' failed.
May 25 21:00:55 main-menu[275]: INFO: Modifying debconf priority limit from 'high' to 'medium'


There is plenty of disk space both in / and in /boot. All the other packages are fetched from the ubuntu archive without any problems. I have tried multiple different archive mirrors, including the base one. I am sort of reaching the end of my wits here.

Also, is there any way to select a different kernel to install from the net installer? kernel-virtual would of course be the first choice.

The main limitation I have is that I only have a non-root shell to the machine, so I cannot install from ISO images, nor do I currently have access to X forwarding so the only way to install is over the internet with --location.

---

### Post by Tuna-Fish on 2018-05-25
Apparently, it was caused by a mistyped console line in the extra-args. That was not fun to debug, especially as the error message did not tell what was wrong.

---


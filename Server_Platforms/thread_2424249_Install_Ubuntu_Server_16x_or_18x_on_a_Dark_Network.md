---
title: "Install Ubuntu Server 16x or 18x on a Dark Network with preseed file"
date: 2019-08-05
forum: Server Platforms
---

### Post by batman182 on 2019-08-05
Hello team,  we have been trying to install ubuntu server 16x or 18x, in a Dark network, that means no Internet Access at all....

It seems to be going fine until it get's stuck in a place, trying to pull some files from internet. (no idea why).

I have made sure the preseed is set no to use or look for upgrades.

I was able to pull the log:

```
Aug  5 13:45:20 anna[3655]: DEBUG: retrieving e2fsprogs-udeb 1.42.13-1ubuntu1Aug  5 13:45:20 anna[3655]: 2019-08-05 13:45:20 URL:http://192.168.46.5/iso/3/files/pool/main/e/e2fsprogs/e2fsprogs-udeb_1.42.13-1ubuntu1_amd64.udeb [257776/257776] -> "/var/cache/anna/e2fsprogs-udeb_1.42.13-1ubuntu1_amd64.udeb" [1]
Aug  5 13:45:21 anna[3655]: DEBUG: retrieving finish-install 2.59ubuntu1
Aug  5 13:45:21 anna[3655]: 2019-08-05 13:45:21 URL:http://192.168.46.5/iso/3/files/pool/main/f/finish-install/finish-install_2.59ubuntu1_all.udeb [26572/26572] -> "/var/cache/anna/finish-install_2.59ubuntu1_all.udeb" [1]
Aug  5 13:45:21 anna[3655]: DEBUG: retrieving firewire-core-modules-4.4.0-142-generic-di 4.4.0-142.168
Aug  5 13:45:21 anna[3655]: http://192.168.46.5/iso/3/files/pool/main/l/linux/firewire-core-modules-4.4.0-142-generic-di_4.4.0-142.168_amd64.udeb:
Aug  5 13:45:21 anna[3655]: 2019-08-05 13:45:21 ERROR 404: Not Found.
Aug  5 13:45:36 anna[3655]: wget: unable to resolve host address 'security.ubuntu.com'
Aug  5 13:45:36 anna[3655]: WARNING **: package retrieval failed
Aug  5 13:46:42 kernel: [  137.036616] random: nonblocking pool is initialized
Aug  5 13:48:12 main-menu[258]: WARNING **: Configuring 'download-installer' failed with error code 6
Aug  5 13:48:12 main-menu[258]: WARNING **: Menu item 'download-installer' failed.
Aug  5 13:48:13 main-menu[258]: INFO: Modifying debconf priority limit from 'high' to 'medium'
Aug  5 13:48:13 debconf: Setting debconf/priority to medium
Aug  5 13:48:14 main-menu[258]: DEBUG: resolver (tzsetup-udeb): package doesn't exist (ignored)
Aug  5 13:48:14 main-menu[258]: DEBUG: resolver (rdate-udeb): package doesn't exist (ignored)
Aug  5 13:48:14 main-menu[258]: DEBUG: resolver (installed-base): package doesn't exist (ignored)
Aug  5 13:48:14 main-menu[258]: DEBUG: resolver (created-fstab): package doesn't exist (ignored)
Aug  5 13:48:14 main-menu[258]: DEBUG: resolver (bootable-system): package doesn't exist (ignored)
Aug  5 13:48:14 main-menu[258]: INFO: Falling back to the package description for brltty-udeb
Aug  5 13:48:27 main-menu[258]: INFO: Falling back to the package description for brltty-udeb
Aug  5 13:48:27 main-menu[258]: INFO: Menu item 'save-logs' selected
```

Basically, everything goes fine, until it tries to locate a file related to firewire, and for some reason it's unable to find it in my network location.

Then it tries to pull it from security.ubuntu.com, but of course, this is a Dark Network, so this will not work at all.

The pressed file contains:

```
# Policy for applying updates. May be "none" (no automatic updates),# "unattended-upgrades" (install security updates automatically), or
# "landscape" (manage system with Landscape).
d-i pkgsel/update-policy select none
```

This is the one I'm using as an example:
[https://github.com/dsgnr/ubuntu-16.04-unattended-install/blob/master/preseed.cfg](https://github.com/dsgnr/ubuntu-16.04-unattended-install/blob/master/preseed.cfg)

Also in the logs I noticed this:
(Full URL to the Image):  [https://ibb.co/8MB82Ky](https://ibb.co/8MB82Ky)
[IMG]https://i.ibb.co/p2PXZ0H/2019-08-05-15-16-44-Win10x64-1709-Upgraded-DO-not-delete-VMware-Remote-Console.png[/IMG]

---


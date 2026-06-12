---
title: "Cloud - network fails in custom images"
date: 2009-12-01
forum: Server Platforms
---

### Post by mozg on 2009-12-01
Hello everyone,

I am experimenting with cloud installation in Ubuntu 9.10. I've successfully setup the controller and couple of nodes and successfully launched the karmic guest images. So the easy part is working fine. However, when I try to customise the image to incorporate the required applications I have a networking problem when starting the new image. Image bundling and registration seems to work fine, the instance boots without problems, but it can't be pinged nor sshed. The console output from the instance shows the network interface as:

----
[    1.757619] e1000 0000:00:03.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, high) -> IRQ 11
[    2.101116] e1000: 0000:00:03.0: e1000_probe: (PCI:33MHz:32-bit) d0:0d:3a:e1:05:f9
[    2.154518] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
----

The other thing that i've noticed is the following messages in the output:

----
mount: mount point /var/run does not exist
mountall: mount /var/run [329] terminated with status 32
mountall: Filesystem could not be mounted: /var/run
mount: mount point /var/lock does not exist
mountall: mount /var/lock [330] terminated with status 32
mountall: Filesystem could not be mounted: /var/lock
mount: mount point /var/run does not exist
mountall: mount /var/run [331] terminated with status 32
mountall: Filesystem could not be mounted: /var/run
mount: mount point /var/lock does not exist
mountall: mount /var/lock [332] terminated with status 32
mountall: Filesystem could not be mounted: /var/lock
----

I am running ubuntu 9.10 amd64 with the latest updates applied to both the controller and the nodes and i've used the Ubuntu guides to create the images.

Did anyone managed to successfully create a custom instance and connect to it? If so, could you please share your steps.

Thanks

---


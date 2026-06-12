---
title: "e1000e module not blacklistable?"
date: 2012-08-25
forum: Server Platforms
---

### Post by realburb on 2012-08-25
Hi, 
I want to passthrough some NICs to my domUs with xen-pciback.
Creating /etc/modprobe.conf with the following options works for my DVB-Card:

```

install ddbridge /sbin/modprobe xen-pciback ; /sbin/modprobe --first-time --ignore-install ddbridge 
options xen-pciback hide=(0000:04:00.0)
```This does not work for the e1000e driver module.

I used the same config, but changed ddbridge to e1000e and another time to e1000 the loading of xen-pciback was not triggerd and the NICs not available for passthrough.

I then removed all the code above from /etc/modprobe.conf and simply put:

```

blacklist e1000e

```and another time

```

blacklist e1000

```in it. After reboot lsmod showed, that e1000e loaded anyway.

After that I removed /etc/modprobe.conf and added the blacklist e1000e command to /etc/modprobe.d/blacklist.conf and another time to /etc/modprobe.d/e1000e.conf . Both times lsmod showed that e1000e was loaded after reboot.

rmmod e1000e works without a problem.

As blacklisting doesnt work, I think the passthrough problem is not related to the way I try to pass it through, but the fact that the e1000e does not respond to any commands at all.

This is what I found about this:

 [https://bugs.launchpad.net/ubuntu/+sux/+bug/226014]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226014")
 [http://linux.koolsolutions.com/2009/ing-in-debian/]("http://linux.koolsolutions.com/2009/10/11/howto-blacklisting-kernel-module-from-auto-loading-in-debian/")


Although I already posted this problem over here:


[http://forum.ubuntuusers.de/topic/modprobe-blacklisting-nicht-mit-e1000e/](http://forum.ubuntuusers.de/topic/modprobe-blacklisting-nicht-mit-e1000e/)

I would be very thankful for any help.

---

### Post by realburb on 2012-08-27
As mentioned in german over here: [http://forum.ubuntuusers.de/topic/modprobe-blacklisting-nicht-mit-e1000e/](http://forum.ubuntuusers.de/topic/modprobe-blacklisting-nicht-mit-e1000e/)
```
sudo update-initramfs -u 
``` worked for the "blacklist e1000e" in /etc/modprobe.conf and /etc/modprobe.d/blacklist.conf or /etc/modprobe.d/e1000e.conf. The driver is not loaded.

Which means the file is read and processed, but when I change "blacklist e1000e" into

```

install e1000e /sbin/modprobe xen-pciback ; /sbin/modprobe --first-time --ignore-install e1000e  
options xen-pciback hide=(0000:01:00.0) 
```

and do another

```
sudo update-initramfs -u 
``` 

No pci devices are assignable nor does lsmod show the xen-pciback driver loaded.

My conclusion would be: This is no problem due to configuration, but something else.

What would be the next steps I can take?

---


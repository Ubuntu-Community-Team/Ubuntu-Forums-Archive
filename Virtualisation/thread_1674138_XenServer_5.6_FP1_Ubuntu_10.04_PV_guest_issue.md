---
title: "XenServer 5.6 FP1 Ubuntu 10.04 PV guest issue"
date: 2011-01-23
forum: Virtualisation
---

### Post by sgjava on 2011-01-23
Followed instructions from [http://www.jansipke.nl/installing-xenserver-tools-on-ubuntu-10-04](http://www.jansipke.nl/installing-xenserver-tools-on-ubuntu-10-04) and Ubuntu 10.04 server fires up and shuts down fine until I add more than one CPU. If there are > one CPUs then the server stays yellow in XenCenter and CPU0 is pegged at 100%. It requires a force shutdown to stop the VM. Once shut down you can remove the extra CPUs and the server shuts down correctly.

Everything works fine if you use the kernel that comes with Ubuntu 10.04.1 server. After doing a sudo apt-get dist-upgrade (before making PV) is when CPU0 starts pegging 100%.

The following works:

initrd.img-2.6.32-24-server
vmlinuz-2.6.32-24-server

The following does not:

initrd.img-2.6.32-27-server
vmlinuz-2.6.32-27-server

Others are having the same issues as noted here [http://forums.citrix.com/thread.jspa?messageID=1524345](http://forums.citrix.com/thread.jspa?messageID=1524345)

Not sure if different kernel is the issue, so I though I'd give it a try here.

Thanks!

---

### Post by sgjava on 2011-01-27
New kernel fixed issue, see [http://forums.citrix.com/thread.jspa?messageID=1527967#1527967](http://forums.citrix.com/thread.jspa?messageID=1527967#1527967)

---

### Post by ShadyB_UK on 2011-01-31
Hi there,

I'm having the same issue with Ubuntu 10.10

Kernel is up to date (2.6.35-25-virtual) and Xen Tools is installed.

All goes well until a reboot/shutdown where the guest will hang indefinitely.

If anyone has a solution I would really appreciate it. 
Been driving me mad for a few days now..

Thanks,
Lee.

---


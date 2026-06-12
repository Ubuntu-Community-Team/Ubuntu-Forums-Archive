---
title: "xen help needed"
date: 2008-01-23
forum: Virtualisation
---

### Post by lcbruzer on 2008-01-23
I've been asked (forced) to start using Xen vice VMware for running RHEL guest VMs.

I installed all the (I believe) appropriate xen packages (below).
I cannot find examples of how to create a new VM and install from DVD using xenman. I also didn't get a new menu item with my installs and must run xenman by hand - but that's OK. 

With xenman - I am able to create/edit a new config file but I must have something wrong in the kernel/ramdisk/phy disk/other parameters. When I try to start the VM I only get a blank screen. In the VM summary the state shows "blocked" (localhost is "running").
I also notice that during the course of the xenman attempt - I believe when I select the "Console" icon after trying to start the guest - I get the following output on my terminal: "sh: /usr/sbin/xenman: not found" but xenman is installed in /usr/bin, not /usr/sbin.

Anyone have a working example to get my started?
I can use either physical device or VBD for the guest.

Thanks in advance!

I have:
Ubuntu 7.10: Linux fryspc 2.6.22-14-xen #1 SMP Tue Dec 18 09:31:59 UTC 2007 i686 GNU/Linux

libc6-xen                                  2.6.1-1ubuntu10
libxen3.1                                  3.1.0-0ubuntu18
linux-headers-2.6.22-14-xen                2.6.22-14.47
linux-image-2.6.22-14-xen                  2.6.22-14.47
linux-image-xen                            2.6.22.14.21
linux-restricted-modules-2.6.22-14-xen     2.6.22.4-14.10
linux-restricted-modules-xen               2.6.22.14.21
linux-ubuntu-modules-2.6.22-14-xen         2.6.22-14.38
linux-xen                                  2.6.22.14.21
python-xen-3.1                             3.1.0-0ubuntu18
ubuntu-xen-desktop                         0.0.1-2ubuntu4
xen-docs-3.1                               3.1.0-0ubuntu18
xen-hypervisor-3.1                         3.1.0-0ubuntu18
xen-ioemu-3.1                              3.1.0-0ubuntu18
xen-tools                                  3.5-1ubuntu2
xen-utils-3.1                              3.1.0-0ubuntu18
xenman                                     0.6-1ubuntu2

---

### Post by lcbruzer on 2008-01-23
Solved:
[http://https://sourceforge.net/forum/forum.php?thread_id=1899423&forum_id=577781]("http://https://sourceforge.net/forum/forum.php?thread_id=1899423&forum_id=577781")

---

### Post by Zenthes on 2008-01-23
> **lcbruzer said:**
> Solved:
[http://https://sourceforge.net/forum/forum.php?thread_id=1899423&forum_id=577781]("http://https://sourceforge.net/forum/forum.php?thread_id=1899423&forum_id=577781")

bad link here, but if your actually interested I'v successfully gotten xen running with ubutnu no problem i just haven't tacked the actual emulation and using xen-tools 

[http://www.howtoforge.com/ubuntu-7.10-server-install-xen-from-ubuntu-repositories](http://www.howtoforge.com/ubuntu-7.10-server-install-xen-from-ubuntu-repositories)

here's a link on installing xen from the repositories 

I'm going to subscribe to this case any more information develops.  I'd work on this project my self but i'v got school work piling up :(

---


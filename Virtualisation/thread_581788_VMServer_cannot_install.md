---
title: "VMServer cannot install"
date: 2007-10-19
forum: Virtualisation
---

### Post by winkerbean on 2007-10-19
I'm trying an apt-get install of vmware-server and vmware-tools-kernel-modules-2.6.20-16, but I get the following output:

Preconfiguring packages ...
**netkit-inetd failed to preconfigure, with exit status 1**
Selecting previously deselected package netkit-inetd.
(Reading database ... 136459 files and directories currently installed.)
Unpacking netkit-inetd (from .../netkit-inetd_0.10-10.3ubuntu4_i386.deb) ...
Selecting previously deselected package vmware-server.
Unpacking vmware-server (from .../vmware-server_1.0.3-1_i386.deb) ...
Selecting previously deselected package vmware-tools-kernel-modules-2.6.20-16.
Unpacking vmware-tools-kernel-modules-2.6.20-16 (from .../vmware-tools-kernel-modules-2.6.20-16_2.6.20.5-16.29_i386.deb) ...
Selecting previously deselected package vmware-tools-kernel-modules.
Unpacking vmware-tools-kernel-modules (from .../vmware-tools-kernel-modules_2.6.20.16.28.1_i386.deb) ...
Setting up netkit-inetd (0.10-10.3ubuntu4) ...
dpkg: error processing netkit-inetd (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of vmware-server:
 vmware-server depends on netkit-inetd | inetd; however:
  Package netkit-inetd is not configured yet.
  Package inetd is not installed.
dpkg: error processing vmware-server (--configure):
 dependency problems - leaving unconfigured
Setting up vmware-tools-kernel-modules-2.6.20-16 (2.6.20.5-16.29) ...

Setting up vmware-tools-kernel-modules (2.6.20.16.28.1) ...
Errors were encountered while processing:
 netkit-inetd
 vmware-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

(Emphasis added by me)

Any suggestions?

---

### Post by bensode on 2007-10-25
Take a look here -- this is what I used 

[http://ubuntu-tutorials.com/2007/09/26/how-to-install-vmware-server-on-ubuntu-710/](http://ubuntu-tutorials.com/2007/09/26/how-to-install-vmware-server-on-ubuntu-710/)

---

### Post by AndyCat on 2007-10-26
Check this  and let me know if it works for you or not.
[http://ubuntuforums.org/showthread.php?t=592636](http://ubuntuforums.org/showthread.php?t=592636)

---


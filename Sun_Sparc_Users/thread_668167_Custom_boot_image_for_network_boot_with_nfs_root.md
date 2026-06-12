---
title: "Custom boot image for network boot with nfs root"
date: 2008-01-15
forum: Sun Sparc Users
---

### Post by pasztorl on 2008-01-15
Hi All!

The offical gutsy boot image for sparc works for me, so I can boot the Sun T1000 from this image served by tftp.
My servers are diskless, so when I installed the base system to an nfs export I need to boot them over network.
I've seen the installer source, and I think I understand the boot image generation clearly.

For testing I generated a boot image from ubuntu stock kernel and initrd image using elftoaout and piggyback64 tools.
When using this boot image I got the following error:

[FONT="Arial Black"]{0} ok boot net0:dhcp

SC Alert: Host System has Reset

SC Alert: Host system has shut down.
\

Sun Fire(TM) T1000, No Keyboard
Copyright 2007 Sun Microsystems, Inc.  All rights reserved.
OpenBoot 4.26.1, 3968 MB memory available, Serial #69311688.
Ethernet address 0:14:4f:21:9c:c8, Host ID: 84219cc8.



Boot device: /pci@7c0/pci@0/network@4:dhcp  File and args:
1000 Mbps full duplex  Link up
Timed out waiting for BOOTP/DHCP reply
ERROR: Last Trap: Fast Data Access MMU Miss

{0} ok
[/FONT]

So, what can I do?
Thanks for your answers,
Lenard

---

### Post by cclub on 2008-01-26
can you confirm serverside that you are getting a DHCP lease? and that it contains the correct information about where the image is located?

---


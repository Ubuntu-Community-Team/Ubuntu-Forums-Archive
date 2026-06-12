---
title: "Best virtualization software for Command line"
date: 2011-08-05
forum: Virtualisation
---

### Post by ddelbarre on 2011-08-05
I have created a virtual test network and machines on an old server using Ubuntu server 11.04 with no GUI running VirtualBox in headless mode with access to the virtual machines via VRDP.  It all works brilliantly except for the fact there's only a license for personal and evaluation use, not commercial use for the access VRDP.  Given theres no gui on the server itself i cannot set up new VMs without VRDP access, ie running Windows setup, which is a pain.

What virtualization software can I use on a CLI only server which would allow me RDP or VNC or some other access to the VMs given that Virtualbox can only do this via the licensed VBExtensions?

I have had a look through the sticky thread, but thats 3 years old almost and i can't find anything i can use searching through the fourms :(

Thanks in advance.

---

### Post by sd33t on 2011-08-05
> **ddelbarre said:**
> ......  It all works brilliantly except for the fact there's only a license for personal and evaluation use, not commercial use for the access VRDP.  Given theres no gui on the server itself i cannot set up new VMs without VRDP access, ie running Windows setup, which is a pain.

What virtualization software can I use on a CLI only server which would allow me RDP or VNC or some other access to the VMs given that Virtualbox can only do this via the licensed VBExtensions?

.....
Thanks in advance.
[LEFT] The terms of VMware Server EULA ***would appear to me*** to be far less restrictive.  You can read it here: [http://www.vmware.com/download/eula/server.html](http://www.vmware.com/download/eula/server.html)  Basically they insist that you only run one host per license.  VMware Server is no longer supported and I had a few issues installing it but I did get it to work nicely.  (the key is finding Firefox v. 3.5 and Foxrunner add on.)   I don't have the hardware to support the new ESXi product.

-Dave
[/LEFT]

---


---
title: "restarting  guest nodes  help!!"
date: 2014-09-13
forum: Virtualisation
---

### Post by n41076jem-2 on 2014-09-13
I let the system upgrade to LTS 14.04.  The computer ran out of disk space, and crashed. I was able to boot the system of a new install thumb drive into recover mode.   I able to recover /var/lib/libvirt directory.

I plan to rebuild the system from scratch.

Can I copy /var/lib/libvirt  back and restart my three guest servers?

Jim

---

### Post by TheFu on 2014-09-14
You need all the libvirt things.  /etc/libvirt/ and to setup the correct groups and install the required packages.

Besides that, it should work. Worse case, you may need to "define" the VMs again. You can do this using virsh define and the XML file for each VM that already exists if they don't show up in virt-manager.

BTW - you can put VM image files on other high performance storage, if you like. It doesn't need to be in /var.

---

### Post by n41076jem-2 on 2014-09-15
Thank been working on getting the images off.  Thanks for reminding me about the etc/libvirt

Jim

---


---
title: "Config / VM locations for libvirtd"
date: 2017-02-25
forum: Virtualisation
---

### Post by jwbrase on 2017-02-25
I recently updated my desktop form Trusty to Xenial. Unfortunately, due to some brokenness in the release upgrade process, I was unable to perform an in-place upgrade, and had to perform a fresh install on a separate partition. I'm in the process of figuring out what system configuration files I had modified and transferring those over from the Trusty partition to the Xenial partition. One thing I'm having to transfer configuration for is libvirtd. I've moved over /etc/libvirt, /var/lib/libvirt, and /var/run/libvirt. Is there anything else I'm not thinking of?

---

### Post by TheFu on 2017-02-25
/etc/libvirt/
You do need to "define" the VMs - shouldn't copy /var/run/ anything.  I'd use **virsh define** for that, but there are multiple ways.
Obviously the VM storage needs to be available and in the place pointed to by the xml file(s) for each VM.  When there are different OSes involved, the virtual hardware emulated by KVM can change change, breaking Windows VMs.  For Linux ones, you probably want the latest emulation.

BTW, I stay with only LTS releases for VMs and VM hosts.

---


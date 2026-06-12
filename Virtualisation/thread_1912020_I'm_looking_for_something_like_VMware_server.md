---
title: "I'm looking for something like VMware server"
date: 2012-01-19
forum: Virtualisation
---

### Post by HHx66 on 2012-01-19
but that will run on Ubuntu 11.10 on kernel 3.0.0-14, I want something with web gui access for my headless server, any ideas?

---

### Post by heshoots67 on 2012-01-19
[http://downloads.vmware.com/d/]("http://downloads.vmware.com/d/")

---

### Post by HHx66 on 2012-01-19
Problem is VMware server doesn't run on 11.10 for some reason, no matter what I try or what patches, I spent about 2 days trying to get it up and running with no success, and as muc has I tried to look into it, theres no web gui or anything for vmware player/etc, unless I am mistaken.

---

### Post by Dangertux on 2012-01-19
Esx + vsphere :-P

Or... KVM and use virt-manager over x forwarded ssh. Still not web based but.. For free it's the only real option you have. I think virtual box has a web GUI as well though I'm not positive.

---

### Post by dcstar on 2012-01-20
> **HHx66 said:**
> Problem is **VMware server doesn't run on 11.10** for some reason, no matter what I try or what patches
.......

Probably because it is obsolete and unsupported.

As already has been posted, VMware ESXI to replace the Ubuntu host install and then install Ubuntu as a VM.

---


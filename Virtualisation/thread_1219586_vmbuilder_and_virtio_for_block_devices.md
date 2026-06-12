---
title: "vmbuilder and virtio for block devices"
date: 2009-07-21
forum: Virtualisation
---

### Post by mknoll on 2009-07-21
I recently install Jaunty, KVM and vmbuilder.  When I create a Jaunty guest with vmbuilder the virtio network device is used, but ide is used instead of virtio for block devices.  Is there a reason virtio isn't used?  Are there concerns with the virtio block device?  Is it safe to use?  Isn't it faster than the ide emulation?

---


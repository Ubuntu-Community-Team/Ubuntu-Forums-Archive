---
title: "KVM: error restoring a deleted image"
date: 2010-01-02
forum: Virtualisation
---

### Post by carnicer on 2010-01-02
Hello,

Not a big deal, I am just playing with KVM before I deploy it into a 15+ developers environment. Using ubuntu server 9.04.

Within **virt-manager**, I have a VM. I *delete* it using the menus (Edit/Delete Virtual Machine). The image is not actually deleted from the images directory, in may case [FONT=Courier New]/var/lib/libvirt/images[/FONT]. Then I try to restore it using File/Restore Saved Machine, i get the following error:


```
Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/manager.py", line 426, in restore_saved_callback
    self.current_connection().restore(file_to_load)
  File "/usr/share/virt-manager/virtManager/connection.py", line 755, in restore
    self.vmm.restore(frm)
  File "/usr/lib/python2.6/dist-packages/libvirt.py", line 1408, in restore
    if ret == -1: raise libvirtError ('virDomainRestore() failed', conn=self)
libvirtError: operation failed: image magic is incorrect

```

---


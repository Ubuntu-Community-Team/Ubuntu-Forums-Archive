---
title: "virt-manager 14.04 client and server bug?"
date: 2014-07-15
forum: Virtualisation
---

### Post by TheFu on 2014-07-15
The vdisk got full today on a VM. During the process of increasing the raw .img file, I've run into a virt-manager issue. The error seen in the virt-manager client is:
> Uncaught error validating hardware input: 'NoneType' object has no attribute 'set_parent'

Detailed error:
```
Uncaught error validating hardware input: 'NoneType' object has no attribute 'set_parent'

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/addhardware.py", line 886, in finish
    if self.validate(notebook.get_current_page()) == False:
  File "/usr/share/virt-manager/virtManager/addhardware.py", line 1214, in validate
    return self.validate_page_storage()
  File "/usr/share/virt-manager/virtManager/addhardware.py", line 1338, in validate_page_storage
    self.conn, disk.path)
  File "/usr/share/virt-manager/virtManager/uihelpers.py", line 894, in check_path_search_for_qemu
    set_error_parent(parent)
  File "/usr/share/virt-manager/virtManager/uihelpers.py", line 49, in set_error_parent
    err_dial.set_parent(parent)
AttributeError: 'NoneType' object has no attribute 'set_parent'

```

This happens when trying to add either a CDROM ISO to the existing VM or when trying to add the larger virtio disk to a new VM.  Basically, I'm stuck in the GUI with no way to get passed the "storage" section.

Trying to connect the 14.04 install ISO (or any other ISO) to a new machine fails in the same way too.

The server is a 14.04 x64 machine.  Virt-manager is running on a x64 14.04 desktop(lxde).  The VM is a 12.04 LXDE x32 VM.  All were current and patched Saturday.

syslog doesn't have anything interesting and libvirt.log doesn't get anything appended when the error is displayed.

Update: Connected the virt-manager to a different KVM/libvirt server (10.04) and had different issues with storage. Couldn't connect an ISO to a pre-existing "CDROM 1" device inside the VM.  Next step is to manually modify the VM XML files to see if it is just the virt-manager GUI or something lower-level.

virt-manager 0.9.5-1ubuntu3.

---


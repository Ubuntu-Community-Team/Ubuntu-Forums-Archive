---
title: "Virsh : error: failed to connect to the hypervisor"
date: 2016-02-04
forum: Virtualisation
---

### Post by hermes5 on 2016-02-04
Hi everyone,

I'm currently attempting a vga passthrough on my macbook pro. I got as far as setting up the windows 8.1 host, ready to passthrough my nvidia card when I hit a roadblock. I needed to update QEMU, I did so, to version 2.1.

Since then, I have been getting the same error message when opening up Virtual Machine Manager.

> Unable to connect to libvirt.

Verify that:
 - The 'libvirt-bin' package is installed
 - The 'libvirtd' daemon has been started
 - You are member of the 'libvirtd' group

Libvirt URI is: qemu:///system

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/connection.py", line
968, in _open_thread
self._backend.open(self._do_creds_password)
  File "/usr/share/virt-manager/virtinst/connection.py", line 158,
in open
    open_flags)
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 105, in
openAuth
    if ret is None:raise libvirtError('virConnectOpenAuth() failed')
libvirtError: Failed to connect socket to '/var/run/libvirt/libvirt
sock': No such file or directory

sorry about the formatting. This is how it appears in the virtual machine connection failure.

I tried 
- reinstalling qemu-kvm packages
- upgrading qemu
- building from source
- purging entire virt setup qemu-kvm libvirt spice etc.

Nothing works...

The output of virsh -c qemu:///session is 

> Welcome to virsh, the virtualisation interactive terminal.

Type:  'help' for help with commands
       'quit' to quit

the out put of virsh -c qemu:///system is

> error: failed to connect to the hypervisor
error: Failed to connect socket to '/var/run/libvirt/libvirt-sock': No such file or directory

I feel like i'm loosing my mind. so very frustrating. 

sudo service libvirt-bin start and stop seem to work, sometimes stop comes out with 

> stop: Unknown instance: 

I found this link,

[http://wiki.libvirt.org/page/Failed_to_connect_to_the_hypervisor](http://wiki.libvirt.org/page/Failed_to_connect_to_the_hypervisor)

But  I havn't been messing around with these settings, so I'm not sure why  they are playing up. I tried restoring them to their defaults, and also  hashing them out, but no change in the error log.

If anyone knows what is up, it would be greatly appreciated if you shared with me. I've searched google and havn't found anything.

---

### Post by TheFu on 2016-02-04
Does everything work without VGA passthru?

---

### Post by hermes5 on 2016-02-04
> **TheFu said:**
> Does everything work without VGA passthru?

Yes, I had the virtio drivers doing their thing with spice being used as the display. I can't get back into virt-manager to see if it was the passthrough that is what broke it.

> $ EDITOR=nano virsh edit windows
error: failed to connect to the hypervisor
error: no valid connection
error: Failed to connect socket to '/var/run/libvirt/libvirt-sock': No such file or directory



---


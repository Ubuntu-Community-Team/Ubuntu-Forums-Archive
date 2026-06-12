---
title: "virt-manager connection error: unable to connect to libvirt"
date: 2014-06-04
forum: Virtualisation
---

### Post by ageeee on 2014-06-04
The configuration is:
Guest: ubuntu 12.04 Desktop, virt-manager installed, network is ok to connect Server with ssh
Server:ubuntu 12.04 Server, libvirt and libvirtd installed, sshd and libvirtd service is running.

I'd like to connect server with virt-manager in guest. Virt-manager is run by root user. 
The virtualization method of server is kvm. The connection method of virt-manager is ssh+kvm.

The detailed error information is: 
```
Unable to connect to libvirt:


Cannot recv data: No protocol specified
No protocol specified


(ssh-askpass:18147): Gtk-WARNING **: cannot open display: :0.0
Permission denied, please try again.
No protocol specified
No protocol specified


(ssh-askpass:18149): Gtk-WARNING **: cannot open display: :0.0
Permission denied, please try again.
No protocol specified
No protocol specified


(ssh-askpass:18151): Gtk-WARNING **: cannot open display: :0.0
Permission denied (publickey,password).
: Connection reset by peer


Verify that:
 - The 'libvirt-bin' package is installed
 - The 'libvirtd' daemon has been started
 - You are member of the 'libvirtd' group


Libvirt URI is: qemu+ssh://john@172.16.106.254/system


Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/connection.py", line 1185, in _open_thread
    self.vmm = self._try_open()
  File "/usr/share/virt-manager/virtManager/connection.py", line 1167, in _try_open
    flags)
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 102, in openAuth
    if ret is None:raise libvirtError('virConnectOpenAuth() failed')
libvirtError: Cannot recv data: No protocol specified
No protocol specified


(ssh-askpass:18147): Gtk-WARNING **: cannot open display: :0.0
Permission denied, please try again.
No protocol specified
No protocol specified


(ssh-askpass:18149): Gtk-WARNING **: cannot open display: :0.0
Permission denied, please try again.
No protocol specified
No protocol specified


(ssh-askpass:18151): Gtk-WARNING **: cannot open display: :0.0
Permission denied (publickey,password).
: Connection reset by peer

```

---

### Post by TheFu on 2014-06-04
Running as root is NOT necessary or really desirable.> 
Verify that:
 - The 'libvirt-bin' package is installed
libvirt must be installed on both the client and server. That is what the error says. Can you validate it is installed?

On the server, the remote userid should be added to the libvirt group and I'd also setup normal ssh key-based login to make life easy.

If you are trying to run the client and server on the same machine, I cannot help. I've never tried that, though I suspect there isn't any need for ssh - after all, the VM is running on the same physical box, so network security isn't a concern.

---

### Post by ageeee on 2014-06-04
Verified that the 'libvirt-bin' package is installed, and libvirt both installed on the client and server sides. 
Add remote userid to libvirt group with '[COLOR=#000000]# usermod -G libvirtd -a [/COLOR]**username**', 
and '[COLOR=#000000] virsh -c qemu+ssh://[/COLOR]**username**[COLOR=#000000]@host1.example.org/system' is able to connect to server.
however virt-manager still failed to do that with errors mentioned above.[/COLOR]

---

### Post by ageeee on 2014-06-04
> **TheFu said:**
> Running as root is NOT necessary or really desirable.
libvirt must be installed on both the client and server. That is what the error says. Can you validate it is installed?

On the server, the remote userid should be added to the libvirt group and I'd also setup normal ssh key-based login to make life easy.

If you are trying to run the client and server on the same machine, I cannot help. I've never tried that, though I suspect there isn't any need for ssh - after all, the VM is running on the same physical box, so network security isn't a concern.

When I run virt-manager as non-root, there is no menu available to connect to remote server. BTW, the client and server are running at different physical machines. The difference is that client machine doesn't support hardware vitualization (ie. vt-x) while the server machine do. I think this will not affect the virt-manager to run since my goal is to use the client to manage remote server instead of implementing virtualization by itself.

---

### Post by ageeee on 2014-06-05
Problem solved with 'virt-manager -c qemu+ssh://username@host1.example.org/system '. It seems that virt-manager must booted with hypervisor specified.

---


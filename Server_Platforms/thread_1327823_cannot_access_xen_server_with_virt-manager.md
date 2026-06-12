---
title: "cannot access xen server with virt-manager"
date: 2009-11-15
forum: Server Platforms
---

### Post by udienz on 2009-11-15
Hi, i have xen server (hardy) and i want to caontrol this server via my pc (hardy). so i install virt-manager. after istalling virt-manager i got error!, here is error code
```

Unable to open a connection to the libvirt management daemon.

Verify that:
 - The 'libvirt-bin' package is installed
 - The 'libvirtd' daemon has been started

Details:
Unable to open connection to hypervisor URI 'xen+ssh://192.168.1.10/':
<class 'libvirt.libvirtError'> cannot recv data: Connection reset by peer
Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/connection.py", line 332, in _open_thread
    self.vmm = libvirt.openReadOnly(self.uri)
  File "/usr/lib/python2.5/site-packages/libvirt.py", line 168, in openReadOnly
    if ret is None:raise libvirtError('virConnectOpenReadOnly() failed')
libvirtError: cannot recv data: Connection reset by peer

```then i checked virtd daemon at my pc
```

udienz@pc:~$ sudo /etc/init.d/libvirt-bin status
 * Checking status of libvirt management daemon libvirtd                                 [ OK ] 
udienz@pc:~$ 

```and also my xen server
```

udienz@xen:~$ sudo /etc/init.d/libvirt-bin status
 * Checking status of libvirt management daemon libvirtd                                 [ OK ] 
udienz@xen:~$ 

```can anyone help me?
:confused:
Note:
* both machine already installed libvirt-bin
* at xen server, root has been added to libvirtd groups
* at xen server running under 2.6.24-24-xen kernel, and my pc running 2.6.24-25-generic kernel

---

### Post by Komir on 2009-11-17
Same problem, any help?

---


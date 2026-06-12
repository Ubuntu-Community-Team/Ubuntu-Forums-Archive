---
title: "Failed to get VNC port"
date: 2017-10-27
forum: Virtualisation
---

### Post by luca-barazzuol on 2017-10-27
Hi,

I have created a VM in kvm using virt-install and the option ```
-graphics none
```
Now I want to add the VNC support so I have edited the xml configuration file and added these lines:
```

    <graphics type='vnc' port='-1' autoport='yes'>
      <listen type='address'/>
    </graphics>

```
I stopped and restart the vm but I get always this error:
```
virsh # vncdisplay my1
error: Failed to get VNC port. Is this domain using VNC?

```
I've also restarted libvitd without success.

The strange things is that I have created a second VM with the option ```
-graphics vnc
```.
The xml file has the same graphics configuration and i can connect via vnc to this machine.

How can I add the support for VNC to my first machine?

Thanks

LK

---

### Post by TheFu on 2017-10-27
Use **virt-manager**.  Create a new VM, point it at a pre-existing VM file/storage.

Using virt-manager, installing a fresh ubuntu should take about 15 min. It is pretty bonehead.  Just be certain to use virtio for storage and network stuff.  If you don't want NAT, setup a Linux bridge BEFORE starting virt-manager and select that for the host networking inside the VM settings.  Virt-manager works to any VM host that supports ssh.  Be certain to setup ssh to the VM host first.  If you use ssh-keys, those will be honored, as will ~/.ssh/config settings.

BTW, VNC is **not** the preferred method to connect to a console since 16.04.  Spice is - that uses the qxl video driver inside the guest (the guest needs to have this driver) and a special Spice client. There is a spice-viewer (I don't remember the actual name, sorry).  Also, this interface is really meant to be used for console access.  If you use virt-manager, the connecton to the remote system will "just work" through an ssh tunnel.

Most administration is performed using ssh in the normal way.  I use "console" access about 3 times on any VM.

IHMO.

---


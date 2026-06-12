---
title: "KVM startup"
date: 2009-11-05
forum: Virtualisation
---

### Post by Komir on 2009-11-05
I create KVM virtual machine (windows xp and fedora 11) with virt-manager. 
Is there any way to autostart that KVM vm on boot of host (Ubuntu 9.10, 64 bit).
If this question been answered, please, show me where?

Sorry for my english! 

P.S. in virt-manager is option "Start virtual machine on host boot up" 
but vm isn't start with host.

---

### Post by jeffblum on 2010-01-10
I'm having the same problem. When I first started using kvm, I could autolaunch virtual machines by checking the box, but now it doesn't work anymore, even for new virtual machines. I've tried via the GUI and the commandline, and they simply won't start when the host machine boots. Also on Ubuntu 9.10 64 bit as host, with guests running pfSense and ubuntu 9.10 server, although the guest doesn't seem to be the issue - it just doesn't even try and start the virtual machines.

---

### Post by ejay563 on 2010-02-12
I'm running Ubuntu Server 9.10, and have no problem autostarting KVM virtual machines with the following method:

1. Use virsh to connect to the local KVM host:
```
$ sudo virsh --connect qemu:///system
Connecting to uri: qemu:///system
Welcome to virsh, the virtualization interactive terminal.

Type:  'help' for help with commands
       'quit' to quit

virsh #
```

2. List all the virtual machines to make sure it is being managed by virsh
```
virsh # list --all
 Id Name                 State
----------------------------------
  1 dns                  running
  2 webserver            running
  3 webserver2           running

```
    2a. If the virtual machine is not currently in virsh, then define it.```
virsh define /etc/libvirt/qemu/<vm-name>.xml
```
3. Set it to autostart.
```
virsh # autostart <vm-name>
```

Let me know if that works.

---

### Post by mvrk on 2010-06-04
anyway to define the order in which the machines start?

---

### Post by josir on 2010-06-28
Hi jeff, 

I encountered the same problem with the same system 9.10 64bits host. 

I tried the autostart from virsh and from GUI but none of them worked.

Did you find any solution or workaround for that?

Thanks in advance,
Josir Gomes

---


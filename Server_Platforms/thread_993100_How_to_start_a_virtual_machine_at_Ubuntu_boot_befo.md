---
title: "How to start a virtual machine at Ubuntu boot before networking service start"
date: 2008-11-25
forum: Server Platforms
---

### Post by dllmetal on 2008-11-25
Hi everyone.

I have Ubuntu server 8.10 installed and VMWare Workstation 6.5 and I wanted to power on an VirtualMachine at boot and only then start the networking service in the physical machine... Possible? How?

Thanks in advance,
Joao Ribeiro

---

### Post by Thirtysixway on 2008-11-25
Under hardware for the virtual machine, can you disable the network adapter?

---

### Post by dllmetal on 2008-11-25
Yes I can do it. But why?

---

### Post by CrucifiedEgo on 2008-11-25
Try in /etc/network/interfaces:
```
auto etho
iface eth0 inet static
[...snip...]
pre-up /usr/local/bin/start-vm.sh
```

then just figure out some way for the shell script to exit once the vm starts (maybe just put the vm in a bg process with & and sleep 60)

EDIT: just a thought.. the vm may start without network interfaces because the virtual devices can't bind to eth0, since it hasn't been brought up yet.  I don't know what what you're suggesting is possible, other than to apply a DROP * firewall, and then open it up after the vm starts.

---

### Post by Philio on 2008-11-25
What are you trying to achieve by doing this?
Do you want networking access within your VM, I would assume that starting it before networking starts would disable the virtual interface and if this is the case you might as well just use the VM without a virtual networking interface?

---

### Post by dllmetal on 2008-11-26
> **Philio said:**
> What are you trying to achieve by doing this?
Do you want networking access within your VM, I would assume that starting it before networking starts would disable the virtual interface and if this is the case you might as well just use the VM without a virtual networking interface?

Well, I have a dhcp server on my virtual machine and I want eth1 in physical pc to receive an ip adress from the VM.

Thanks

---

### Post by dllmetal on 2008-11-26
Hi again,

The thing is that I have to physical network cards and two virtual.


eth0 is binded with vm-eth0
eth1 is binded with vm-eth1

My Virtual Machine is a proxy and dhcp server and as eth1 is set to dhcp, if the virtual machine dhcp server isn't up then eth1 on physical will be deactivated and my network want work.

I though of calling vm and then dhclient eth1 but I don't know what files to edit and dhclient should also need sudo permissions to go on.

What can I do??

Thanks

---


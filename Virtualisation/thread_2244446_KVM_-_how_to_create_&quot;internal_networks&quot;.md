---
title: "KVM - how to create &quot;internal networks&quot;?"
date: 2014-09-16
forum: Virtualisation
---

### Post by Remten on 2014-09-16
In kvm/qemu, how do you create VirtualBox-style "internal networks"?


If using VirtualBox, you would easily be able to do something like this (from a dedoimedo tutorial article):
[IMG]http://www.dedoimedo.com/images/computers_new_1/virtualbox-network-internal.png[/IMG]
[http://www.dedoimedo.com/computers/virtualbox-network-sharing.html](http://www.dedoimedo.com/computers/virtualbox-network-sharing.html)


How do you achieve something similar with kvm?

---

### Post by TheFu on 2014-09-17
Most networking for KVM is handled better outside the tool using the brtutils package and nominal Linux bridges.
In recent libvirt releases, they have created a NAT network as part of the install, so you might be able to use that.  

The settings for that is at the VM host level, not per VM.  
* Right click on the hostOS inside virt-manager, 
* Details
* Network Interfaces

---

### Post by bjdea1 on 2014-09-30
Whenever I use KVM I do not use any of the provided management tools (GUI), instead I do everything from the command line, using the qemu-kvm command. For example:

/usr/libexec/qemu-kvm -drive file=/vz/kvm/vmdata.qcow2,cache=none -m 2000 -smp 2 -net nic,model=rtl8139,macaddr=52:54:00:12:34:11,vlan=0 -net tap,script=no,ifname=tap0,vlan=0 --daemonize

This starts the VM up with a network adapter connected to a tap device on the host machine. So you also need to setup the tap device PRIOR to running the above command. In the command above we gave it tap device "tap0", so we need to set this up beforehand using tunctl command.

This should give you network connectivity between the host and VM - a local network.

---


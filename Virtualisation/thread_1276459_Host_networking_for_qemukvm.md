---
title: "Host networking for qemu/kvm"
date: 2009-09-27
forum: Virtualisation
---

### Post by noorez on 2009-09-27
Hi,

I am currently experimenting with kvm/qemu and virtual-machine-manager 
for a virtual machine and I would like to try installing the Ubuntu 9.04 server. However, I'm having some trouble with setting up the networking. I found a solution that was used with VirtualBox using TAP. This is the setup that was used in /etc/network/interfaces:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
# auto lo
# iface lo inet loopback

auto lo
iface lo inet loopback

iface eth0 inet static
address eth0 192.168.2.2
netmask 255.255.255.0
gateway 192.168.2.1

auto tap0
iface tap0 inet manual
tunctl_user noorez

auto tap1
iface tap1 inet manual
tunctl_user noorez

auto br0
iface br0 inet static
address 192.168.2.2
netmask 255.255.255.0
gateway 192.168.2.1
bridge_ports eth0 tap0 tap1
bridge_maxwait 0

```

Would this work for kvm/qemu as well?

Also, during setup of the virtual machine, what device would I select? When I configure the virtual machine with 'Shared Physical Device', would I be selecting tap0(Bridge br0) ?

I have seen some other solutions with tap on google where people create a script to setup the bridge and then pass
-net tap to qemu to start the virtual machine with a tap interface but since I am using the virtual machine manager would I need to have the tap0,tap1.... preconfigured in /etc/network/interfaces

---

### Post by bodhi.zazen on 2009-09-27
This is how I do it :

[http://blog.bodhizazen.net/linux/virt-manager-bridged-networking/](http://blog.bodhizazen.net/linux/virt-manager-bridged-networking/)

[http://blog.bodhizazen.net/linux/kvm_network_scripts/](http://blog.bodhizazen.net/linux/kvm_network_scripts/)

The first link is with Virtmanager, the second link is if you use KVM directly from the command line (it is a little wrapper script). You can modify those if needed.

---

### Post by noorez on 2009-09-27
The above websites did help out.

Although...there is still the issue of having the scripts....and also, the virt-manager did not allow me to choose some options that I would have liked.
I tried the /etc/networ/interface file I gave the first time:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
# auto lo
# iface lo inet loopback

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static

auto tap0
iface tap0 inet manual
tunctl_user noorez

auto tap1
iface tap1 inet manual
tunctl_user noorez

auto br0
iface br0 inet static
address 192.168.2.2
netmask 255.255.255.0
gateway 192.168.2.1
bridge_ports eth0 tap0 tap1
bridge_maxwait 0

```

and this time gave the command line:
```

qemu -M pc -m 512 -kernel-kqemu -usb -no-acpi -hda /home/noorez/Linux -localtime -cdrom /home/noorez/ubuntu-9.04-dvd-i386.iso -net nic,vlan=0 -net tap,vlan=0,fd=tap0,script=no  -net nic,vlan=0 -net tap,vlan=0,fd=tap1 -monitor pty -boot d

```

For each nic, i simply gave the name fd=tap0 and tap1 and did not give any scripts to execute since the tap interfaces will always stay there.

Would this cause any problems? Is there something that I might have missed?

---

### Post by bodhi.zazen on 2009-09-27
You should be fine.

---


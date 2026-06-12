---
title: "[KVM]Guest starts, Host lost its connectivity"
date: 2010-11-12
forum: Virtualisation
---

### Post by bofeng on 2010-11-12
[SIZE=4][FONT=Times New Roman]Hello, all professionals
I followed the tutorial in Ubuntu documentation about how to setup and run a Virtual Machines in KVM(only).

Here is what I did:[/FONT][/SIZE]
```

[LIST=1]
[*]Add a bridge(let's say br0)
[*]Join the bridge to my Wired Connection Interface(eth0)
[*]Add a tap interface(let's say tap0)
[*]Join the bridge to the tap0
[*]start the Virtual Machine with option: -net nic, -net tap,ifname=tap0
[/LIST]

```

[SIZE=4][FONT=Times New Roman]After I boot the Virtual Machine, it can connect to the outside world. However, my host lost its connectivity unless I delete the bridge br0.

Wrap up, every time I add a bridge and join my eth0 interface, my Host will definitely lose its connectivity.:(

I am waiting for the tips, and I appreciate your kind-hearted aids.
Respectfully

[/FONT][/SIZE]

---

### Post by gdahlm on 2010-11-12
can you please post the contents of your /etc/network/interfaces file?

mine will be at the end of this message, although I do have to warn you that the bridged interface does break NetworkManager in pretty ugly ways.

If you desire to use wireless connectivity or connect to VPN's via the default gnome interface it is better to run the natted bridge.

are you using libvirt or pure kvm?

If you are using libvirt can you please paste a copy from the command "virsh dumpxml domain" where domain is the name of the guest?


gdahlm@anathema:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback
auto eth1
iface eth1 inet manual
up ifconfig eth1 0.0.0.0 up
up ip link set eth1 promisc on
down ip link set eth1 promisc off
down ifconfig eth1 down


auto br0
iface br0 inet static
address 192.168.2.20
netmask 255.255.255.0
broadcast 192.168.2.255
gateway 192.168.2.1
# Ports you want to add to your bridge
bridge_ports eth1 
# Time to wait before loading the bridge
bridge_maxwait 0

---


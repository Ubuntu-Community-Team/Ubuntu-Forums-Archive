---
title: "trying to setup VLAN over bond - getting error"
date: 2013-04-08
forum: Server Platforms
---

### Post by nicolasdiogo on 2013-04-08
hello

i would like to setup a bonded connection that requires to have access to 3 different networks where 2 are tagged - 10,20

i have created the bond0 with :

```

auto bond0
iface bond0 inet manual
hwaddress ether 00:02:A3:48:50:2D
bond-mode 4
bond-miimon 100
bond_mode 802.3ad
slaves eth1

```

i have then tried to created a vlan with:
```

modprobe 8021q
vconfig add bond0 10

```


however, that returns the following error:
```

ERROR: trying to add VLAN #10 to IF -:bond0:-  error: Operation not supported

```

not sure what the correct process for creating this setup would be.

i would appreciate some assistance.

thanks,

---

### Post by darkod on 2013-04-08
First of all, is bond0 working correctly?

If it is, I think the first option to try is configuring VLANs like described in the first post here:
[http://ubuntuforums.org/showthread.php?t=703387](http://ubuntuforums.org/showthread.php?t=703387)

So, you would have like three separate interfaces each with its own IP address, subnet, etc. The interfaces would be bond0, bond0.10 and bond0.20.

Try that.

---

### Post by darkod on 2013-04-08
I also noticed you have a syntax error in the option:
bond_mode 802.3ad

It should be bond-mode but you have it above anyway. Whether you use 802.3ad or 4 it's the same. You only need the option once and the correct syntax is bond-mode.

Not sue if that can affect it.
[https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

---

### Post by darkod on 2013-04-08
Also, are you sure there is option 'slaves' like you are using it?

There is one called bond-slaves and they seem to suggest the value 'none', like:
bond-slaves none

But not only slaves.

---

### Post by nicolasdiogo on 2013-04-08
thanks for the input guys - i am checking the system now.

---

### Post by nicolasdiogo on 2013-04-09
hello,

just an update.

i hope this time - you will agree that this is a correct configuration for the system (!fingers crossed)

i have researched and now have the system working with the following setup:

```

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto eth1
iface eth1 inet manual

# bond0 network interface
auto bond0
iface bond0 inet manual
        bond_mode 0
        bond_miimon 200
        bond_updelay 200
        bond_downdelay 200
        bond_xmit_hash_policy layer2+3
        bond_lacp_rate slow
        bond-slaves eth0 eth1

auto virbr0
iface virbr0 inet static
        address 192.168.1.3
        gateway 192.168.1.1
        netmask 255.255.255.0
        broadcast 192.168.1.255
        network 192.168.1.0
        bridge_ports bond0
        pre-up brctl addbr br0

auto virbr10
iface virbr10 inet static
        address 10.0.10.3
        netmask 255.255.255.0
        broadcast 10.0.10.255
        network 10.0.10.0
        vlan-raw-device bond0
        bridge_ports bond0.10
        bridge_stp off

```


i really liked the simplicity of the setup - particularly with the vlan incorporated into the bridge:
```

...
        vlan-raw-device bond0
        bridge_ports bond0.10
...

```

that i have found on a post at:
[http://vk5fj.blogspot.co.uk/2012/04/vm-on-kvm-on-vlan-on-bridge-interface.html](http://vk5fj.blogspot.co.uk/2012/04/vm-on-kvm-on-vlan-on-bridge-interface.html)

is this a correct setup?
i will be monitoring and posting back.

thanks,

---

### Post by darkod on 2013-04-09
looks OK but why did you use bridges? Are you using a VM too because that wasn't meantioned in your original post.

If this is only a physical server, you need only bonding without the bridging. So, you need to simply bond0, bond0.10, bond0.20, etc.

---

### Post by nicolasdiogo on 2013-04-09
sorry darkod

the original idea was to use this as a storage only system.
but i have added a single VM (kvm) to manage the other nodes of the cluster (opennebulla).

thanks,

---

### Post by nicolasdiogo on 2013-04-11
just a quick note to say that 'aparently' it is not a good idea to use a bond with mode 0 (ZERO)

see these links:

[https://access.redhat.com/site/articles/16039](https://access.redhat.com/site/articles/16039)
[http://forum.proxmox.com/threads/2676-bonding-bridging-freez](http://forum.proxmox.com/threads/2676-bonding-bridging-freez)

---


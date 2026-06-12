---
title: "setup bridge on kvm with ubuntu server 8.04"
date: 2008-08-05
forum: Virtualisation
---

### Post by crewmanjoo on 2008-08-05
Hi all,

I have an install of KVM with virtmanager on ubuntu server 8.04. I succesfully installed a virtual machine and all is running great.

The problem I am having is setting up a public bridge so I can see and ping the virtual machine on the network. I have given both the virtual server and the single virtual machine unique IP addresses. I can ping and connect to the virtual server no problem. But I cant ping the virtual machine.

I setup a bridge interface edit /etc/network/interfaces with correct IP and network settting as mentioned here
[https://help.ubuntu.com/community/KVM#Creating%20a%20network%20bridge%20on%20the%20host](https://help.ubuntu.com/community/KVM#Creating%20a%20network%20bridge%20on%20the%20host)

So something like:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
        address 192.168.0.10
        network 192.168.0.0
        netmask 255.255.255.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

How do I make the virtual machines use the bridge?  There is no xml config file in the path /etc/libvirt/qemu/. Im a bit confused.

---

### Post by jurrit on 2008-08-08
According to : [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

You need to do the following:

Virtual machines are defined in XML files; ubuntu-vm-builder, the tool we will use to create VMs, bases them on the template file /usr/share/ubuntu-vm-builder/templates/libvirt.tmpl. Open that file, and change:

```
    <interface type='network'>
      <mac address='%MAC%'/>
      <source network='default'/>
    </interface>
```

To:

```
    <interface type='bridge'>
      <mac address='%MAC%'/>
      <source bridge='br0'/>
    </interface>
```

---

### Post by eholcroft on 2009-05-12
Like he said, there IS NO xml file to edit. Is there some reason why the xml profile is not being generated?

---

### Post by Pnuts on 2009-05-12
IM still learning this as I go, but from what I see above, he is using virt-manager to create the images and not the ubuntu-vm-builder. I do not know the answer but assume it is done a different way.

---

### Post by bodhi.zazen on 2009-05-12
Personally I user KVM directly, and I wrote a wrapper script , posted it here :

[https://help.ubuntu.com/community/KVM/Directly](https://help.ubuntu.com/community/KVM/Directly)

---


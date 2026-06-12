---
title: "libvirt and real addresses"
date: 2009-03-03
forum: Virtualisation
---

### Post by Looooooka on 2009-03-03
so i have a server that is running on a real ip address(NOT LAN IP)
and i want to enable the virtual machines to use real addresses as well.Oh...212.x.x.126 is the psychical gateway address for internet access and we use 255.255.255.192 as the netmask(totally in the hands of the provider...)
I have this going with the following configuration:
interfaces config file:
```

# The loopback network interface
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
        address 192.168.0.2
        netmask 255.255.255.0

# The primary network interface
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
        address 212.x.x.121
        netmask 255.255.255.192
        network 212.x.x.0
        broadcast 212.x.x.255
        gateway 212.x.x.126
        dns-nameservers 212.x.x.116
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

```





default.xml:
```

<network>
  <name>default</name>
  <uuid></uuid>
<forward dev='eth0' mode='nat'/>
  <bridge name='br0' stp='on' forwardDelay='0'/>
  <ip address='212.x.x.122' netmask='255.255.255.192'>
    <dhcp>
      <range start='212.x.x.123' end='212.x.x.124' />
        <host mac='00:40:58:44:86:60' ip='212.x.x.123' />
</dhcp>
  </ip>
</network>



```

and finally the network section of the virtual machine:
```

    <interface type='bridge'>
      <mac address='00:40:58:44:86:60'/>
      <source bridge='br0'/>
<target dev="tap0"/>
      <model type='virtio'/>
    </interface>

```
well...dhcp doesn't work but if i set the guest to 212.x.x.123 and give him the same gateway the host is using it ALL works.
The problem is the 212.x.x.122 address is being wasted on the tun0 device which the guest uses to connect.I tried setting it to the same ip as the guest and ofcourse then the guest has NO network connectivity.
This wouldn't be a big deal if these were LAN addresses because u can waste those as much as you want.

so my question is...is there any way to make this work without wasting one ip?

Perhaps setting the tun0 to a LAN IP and libvirt could add it to the br0 bridge...and magically make it work through a few iptables rules?

If anyone can help with the following:

-server has it's own actual ipaddress on eth0(bridged or not i don't care)
-server has multiple virtual machines and they each have their OWN REAL IP
-no IP is wasted for tunx brx or any sort of other magic network devices used for this to work.

THANKS!

---

### Post by Looooooka on 2009-03-03
never mind...it seems i CAN set the tap device to a lan ip...the problem appears with the 122 address i'm trying to use.Can't use it even on an actual host machine.Time to bug the provider in the morning :)
However the thing that still bothers me is that dhcp doesn't work.
Is there anything special one needs to do to get this working?
like...actually install a dhcp server and have it somehow use the libvirt settings?

---


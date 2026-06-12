---
title: "Trying to setup a bridged network - fails"
date: 2017-05-30
forum: Server Platforms
---

### Post by mattiash on 2017-05-30
I have just installed a brand new Ubuntu Server 16.04 LTS to use as among other things a VM host.
Therefor I need to bridge my only network interface. I have googled and tried a couple of solutions... 
But all it does it render my server unreachable, it gets a DHCP lease from my dhcp-server.

This is my config atm:
```


[LIST]
[*]# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto br0
iface br0 inet dhcp
[/LIST]

```

My network nic isn't br0... oh wait. I have to use a static address havn't I? To tell what to bridge?

---

### Post by mattiash on 2017-05-30
This is my new interfaces config:
```

[COLOR=#4D2F2D][FONT=Courier]iface br0 inet static[/FONT][/COLOR]
[COLOR=#4D2F2D][FONT=Courier]        address 192.168.1.50[/FONT][/COLOR]
[COLOR=#4D2F2D][FONT=Courier]        netmask 255.255.255.0[/FONT][/COLOR]
[COLOR=#4D2F2D][FONT=Courier]        network 192.168.1.0[/FONT][/COLOR]
[COLOR=#4D2F2D][FONT=Courier]        broadcast 192.168.1.255[/FONT][/COLOR]
[COLOR=#4D2F2D][FONT=Courier]        gateway 192.168.1.1[/FONT][/COLOR]
[COLOR=#4D2F2D][FONT=Courier]        bridge_ports enp0s31f6[/FONT][/COLOR]
[COLOR=#4D2F2D][FONT=Courier]        bridge_stp off[/FONT][/COLOR]
[COLOR=#4D2F2D][FONT=Courier]        bridge_maxwait 5[/FONT][/COLOR]
[COLOR=#4D2F2D][FONT=Courier]        # dns-* options are implemented by the resolvconf package, if installed[/FONT][/COLOR]
[COLOR=#4D2F2D][FONT=Courier]        dns-nameservers 192.168.1.1[/FONT][/COLOR]

```

Does this work you think?

---

### Post by mattiash on 2017-05-30
So that worked... but now to the real question... how do I setup a network connection for a VM?

---

### Post by darkod on 2017-05-30
What do you mean how to set up a network connection? Did you try creating a VM at all?

During the creation for the network options just select br0 and the virtual NIC will be attached to br0, in other words the virtual NIC will be in your LAN 192.168.1.0/24. Just like the VM is plugged directly in your router.

---

### Post by mattiash on 2017-05-30
Ofc! Thank you! Now it is working so beautiful. :)

---


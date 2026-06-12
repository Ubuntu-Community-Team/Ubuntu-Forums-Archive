---
title: "UEC nodes can not access internet"
date: 2010-10-14
forum: Ubuntu Cloud and Juju
---

### Post by ganyx on 2010-10-14
```
Solved
Added 18.10:
This is solved. 
At Front Node, edit file /etc/rc.local by adding one line
[CODE]
/sbin/iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -o eth1 -j MASQUERADE

```
[/CODE]

Hi

I have installed the UEC (Ubuntu Server Version 10.10) for our cluster, the front node seems to work fine. The nodes behind the switcher can ping between nodes but can not ping the ip outside the local network.

After a default installation of UEC, the cloud seems to be alright. But I will need the internet access from the nodes to update my base system.

I have set as follow
Front node: eth0 192.168.1.1, (with eth1 pointing to the public network)
compute node 1: eth0 192.168.1.2

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
        address 192.168.1.2
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 129.78.142.176
        dns-search pgcluster.civil.usyd.edu.au
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

```

Anyone have an idea to solve this problem? Thanks!

---

### Post by ganyx on 2010-10-15
the route information is
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.0   U     0      0        0 eth1
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         br-j03-1.civil. 0.0.0.0         UG    100    0        0 eth1

```

---

### Post by Daviey on 2010-10-15
@ganyx, can you clarify your topology.

So you have an 'all in one (excluding nodes)' and separate nodes.  I'm trying to determine where the issue could be.

Do you have, as you described, 'front nodes' that are working as they should... And some additional nodes behind a router?

Thanks.

---

### Post by kim0 on 2010-10-15
Can you please explain your setup in more detail

- How many machines are you using
- How are they connected (switch/router)? Ascii art ? :)
- ip configurations and route tables would be awesome

---

### Post by ganyx on 2010-10-15
Hi thank you for your reply!

the topology is
eth0 of all nodes connected to swither
eth1 of the front node connected to internet

I have 5 machines, each one has 24 CPUs. They are connected through the switcher, and 4 nodes behind the switcher should be connected through the front node.

Now these 5 nodes can ping and ssh with one another, but the 4 nodes behind the switcher can not ping any ip outside this local network.

I hope this will clarify something. Please let me know what other information I should provide to solve this problem.

Thank you!

---


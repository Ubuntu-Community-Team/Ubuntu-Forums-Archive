---
title: "KVM - Public IP Problem"
date: 2014-06-04
forum: Virtualisation
---

### Post by E_W on 2014-06-04
Hey, 


I have some problems with kvm and public ips. 


my current host setup:

[LIST]
[*]Ubuntu 14.04 LTS (Server)
[*]2 NICs
[LIST]
[*]1 nic with public ip address. from isp via dhcp
[*]1 nic with private network from (my) dhcp
[/LIST]
[/LIST]


I installed freebsd in a vm and  on each physical interface created one virtual for the vm. 
on the "private" side all works fine. 
but on the public site some problems. 
the vm got a public ip from ISPs dhcp server, but no internet connection.  
neither from vm > internet nor from internet >  vm. 


i think it is some routing problems but no idea how to fix it. 


can anyone help me ?

---

### Post by TheFu on 2014-06-04
Please post the output of **route** from every machine involved.

---

### Post by E_W on 2014-06-04
hey , thanks for the quick reply :)[B]

KVM-Host:[/B]


**$ route **
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.10.0.1       0.0.0.0         UG    0      0        0 p4p1
10.10.0.0       *               255.255.0.0     U     0      0        0 p4p1
192.168.122.0   *               255.255.255.0   U     0      0        0 virbr0
X.X.XXX.128     *               255.255.255.192 U     0      0        0 p1p1

```


routing table for second gateway 
**$ ip route list table rt2 **
```
default via X.X.XXX.129 dev p1p1 


X.X.XXX.128/26 dev p1p1  scope link  src X.X.XXX.164
```




**$ ip rule show**
```
0:    from all lookup local 32764:    from all to X.X.XXX.164 lookup rt2 
32765:    from X.X.XXX.164 lookup rt2 
32766:    from all lookup main 
32767:    from all lookup default
```




_**BSD Client: **_


```

Destination        Gateway                Flags    Refs    Use        Mtu        Netif    Expire
default            X.X.XXX.129        UGS        0        1030    1500    vtnet0     
10.10.0.0/16    link#2                U        0        2889    1500    em0     
10.10.3.129        link#2                UHS        0        0        16384    lo0     
YY.YY.43.62        52:54:00:cd:18:2d    UHS        0        235        1500    vtnet0     
ZZ.ZZZ.62.62    52:54:00:cd:18:2d    UHS        0        236        1500    vtnet0     
127.0.0.1        link#5                UH        0        119        16384    lo0     
X.X.XXX.128/26    link#1                U        0        1696    1500    vtnet0     
X.X.XXX.133        link#1                UHS        0        0        16384    lo0     
```

---

### Post by TheFu on 2014-06-05
Holy crap batman!
I'm gonna need a picture.
You're doing things - or trying to do things - I've never attempted.

BTW, the hostOS doesn't need any IP config on the WAN port if you want to run a router distro inside a VM. Setup a standard Linux bridge for that - actually, I use standard Linux bridging for everything.  Never found the "built-in" VM networking to be useful - I ignore it completely.

---

### Post by E_W on 2014-06-06
Okay, I have tried it with new config using bridge device. 
and also using linux as client instead of bsd 

```

auto br0 
iface br0 inet dhcp
    bridge_ports    p1p1
    bridge_stp      off
    bridge_maxwait  0
    bridge_fd       0



```

One machine  working out of the box. YEAH :D 
but a second machine with the exactly same config except a different mac address dont. the same problem as with bsd...


Host:

[IMG]http://abload.de/img/hvopxc.png[/IMG]

vm work:
[IMG]http://abload.de/img/wc2xphx.png[/IMG]



vm does not work:
[IMG]http://abload.de/img/nwch9p6w.png[/IMG]



I have no idea whats the problem. looks like the same config for me -.-.  I  have tried to add routes to clients with this command: [COLOR=#434656]route add -host <ip-of-client> dev br0 without success. [/COLOR]

---

### Post by TheFu on 2014-06-06
Please post the entire /etc/network/interfaces file from the host - unmodified. Text is much preferred in CODE tags, not images. I'm having an issue translating the blacked out parts too - my brain just can't do that. Sorry for my failure.

---

### Post by E_W on 2014-06-06
Okay. 
```

# The loopback network interface
auto lo
iface lo inet loopback



auto br0 
iface br0 inet dhcp
    bridge_ports    p1p1
    bridge_stp      off
    bridge_maxwait  0
    bridge_fd       0




auto br1
iface br1 inet static


    bridge_ports    p4p1
    bridge_stp      off
    bridge_maxwait  0
    bridge_fd       0
    address 10.10.0.5
    netmask 255.255.0.0

```


Host: 
```

r1co@kvm-host:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         222.8.48.129    0.0.0.0         UG    0      0        0 br0
10.10.0.0       0.0.0.0         255.255.0.0     U     0      0        0 br1
222.8.48.128    0.0.0.0         255.255.255.192 U     0      0        0 br0

```


vm1 (working): 
```

r1co@vm1:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         222.8.48.129    0.0.0.0         UG    0      0        0 eth0
222.8.48.128    0.0.0.0         255.255.255.192 U     0      0        0 eth0




```


vm2 (not working):
```

r1co@vm1:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         222.8.48.129    0.0.0.0         UG    0      0        0 eth0
222.8.48.128    0.0.0.0         255.255.255.192 U     0      0        0 eth0




```

---

### Post by TheFu on 2014-06-06
You need stanzas for 
p1p1 and p4p1.

This is what those look like on a KVM host with eth0 as the NIC.  eth0 is NOT used directly for anything.
```
auto eth0
iface eth0 inet manual
```

---

### Post by E_W on 2014-06-06
okay. /etc/network/interfaces now looks like this: 

```

# The loopback network interface
auto lo
iface lo inet loopback




auto p1p1
iface p1p1 inet manual


auto p4p1
iface p4p1 inet manual




auto br0 
iface br0 inet dhcp
    bridge_ports    p1p1
    bridge_stp      off
    bridge_maxwait  0
    bridge_fd       0




auto br1
iface br1 inet static
    bridge_ports    p4p1
    bridge_stp      off
    bridge_maxwait  0
    bridge_fd       0
    address 10.10.0.5
    netmask 255.255.0.0



```


still the same problem.
do you have any other ideas?

---

### Post by TheFu on 2014-06-06
Besides verifying the ethernet device names - I don't have anything.  I'm used to eth0/eth1/eth2 ... devices.  Is this on a 14.04 box with the new BSD-style network device names?

BTW, I have a few VMs (20-30) setup using Linux bridges. Here's a working example:
```
auto br0
iface br0 inet static
  address 172.22.22.6
  gateway 172.22.22.1
  netmask 255.255.255.0
  broadcast 172.22.22.255
  # mtu 9014
  dns-nameservers 172.22.22.1
  bridge_ports eth0
  bridge_fd 9
  bridge_hello 2
  bridge_maxage 12
  bridge_stp off

auto eth1
iface eth1 inet manual
auto br1
iface br1 inet manual
  bridge_ports eth1
  bridge_fd 9
  bridge_stp off
```

For DNS to work on 12.04 and later, the dns-nameservers  needs to be here if there is an IP assigned for the hostOS to use as well.
For non-IP assigned bridges ... just the minimal settings above for eth1 work.

---

### Post by E_W on 2014-06-13
Problem solved -.-
my isp is the problem. two of the assigned ips dont work correct. 
tried some others from the list. now it works without any problems ...


> Besides verifying the ethernet device names - I don't have anything. I'm used to eth0/eth1/eth2 ... devices. Is this on a 14.04 box with the new BSD-style network device names?

i think because of uefi bios. i have the same interface names with 13.04

---


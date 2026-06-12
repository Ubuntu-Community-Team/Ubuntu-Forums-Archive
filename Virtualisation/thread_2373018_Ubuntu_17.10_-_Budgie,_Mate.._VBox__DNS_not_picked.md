---
title: "Ubuntu 17.10 - Budgie, Mate.. VBox : DNS not picked up from interfaces"
date: 2017-10-01
forum: Virtualisation
---

### Post by holiday on 2017-10-01
17.10 budgie,mate,lubuntu

Removed NetworkManager -- requirement.    

**VBox network    
-adapter1 host-only
-adapter2 bridged

/etc/network/interfaces

```
# interfaces(5) file used by ifup(8) and ifdown(8)

auto lo
iface lo inet loopback

auto enp0s8
  iface enp0s8 inet static
  address 192.168.56.123

auto enp0s3
  iface enp0s3 inet static
  address 192.168.0.123
  netmask 255.255.255.0
  gateway 192.168.0.1
  dns-nameservers 8.8.8.8  8.8.4.4


```

```

 cat /etc/resolv.conf

nameserver 8.8.8.8
nameserver 8.8.4.4
nameserver 127.0.0.53


```

I have a few VMs, a mix of 17.04 and 17.10. The 17.04s work with this config but the 17.10s do not.
The 17.10s can commuicate with the 192.168* subnets as expected but can't get outside the LAN by either hostname or IP address. 

Route from working 17.04 host;
```
default via 192.168.0.1 dev enp0s3 onlink 
192.168.0.0/24 dev enp0s3 proto kernel scope link src 192.168.0.124 
192.168.56.0/24 dev enp0s8 proto kernel scope link src 192.168.56.124 

test@test:~$ ping -c1 ubuntu.com | grep received
1 packets transmitted, 1 received, 0% packet loss, time 0ms

```


And now from failing host 

```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto enp0s8
  iface enp0s8 inet static
  address 192.168.56.123

auto enp0s3
  iface enp0s3 inet static
  address 192.168.0.123
  netmask 255.255.255.0
  gateway 192.168.0.1
  dns-nameservers 8.8.8.8  8.8.4.4

```

```

# This file is managed by man:systemd-resolved(8). Do not edit.
#
# 127.0.0.53 is the systemd-resolved stub resolver.
# run "systemd-resolve --status" to see details about the actual nameservers.
nameserver 127.0.0.53


```

ip route

```
default via 192.168.0.1 dev enp0s3 onlink 
169.254.0.0/16 dev enp0s3 scope link metric 1000 
192.168.0.0/24 dev enp0s3 proto kernel scope link src 192.168.0.123 
192.168.56.0/24 dev enp0s8 proto kernel scope link src 192.168.56.123 

```

```

ping -c1 ubuntu.com | grep received
ping: ubuntu.com: Temporary failure in name resolution

```

Ok so let's get rid of that extra route that the working config doesn't have 

```

# ip route del 169.254.0.0/16
# ip route
default via 192.168.0.1 dev enp0s3 onlink 
192.168.0.0/24 dev enp0s3 proto kernel scope link src 192.168.0.123 
192.168.56.0/24 dev enp0s8 proto kernel scope link src 192.168.56.123 
# ping -c1 ubuntu.com | grep received
ping: ubuntu.com: Temporary failure in name resolution

```

Well are the links working at all? Let's check the gateways and the interfaces on the *.123 host.

```

ping -c1 192.168.1 | grep received
1 packets transmitted, 1 received, 0% packet loss, time 0ms
# ping -c1 192.168.123 | grep received
1 packets transmitted, 1 received, 0% packet loss, time 0ms
# ping -c1 192.168.56.123 | grep received
1 packets transmitted, 1 received, 0% packet loss, time 0ms
# ping -c1 192.168.56.1 | grep received
1 packets transmitted, 1 received, 0% packet loss, time 0ms

```


So what's going on? Where to look next. 
I've searched the bug reports for 17.10 and haven't seen anything there so .... 

Well I don't know. If anyone sees anything here let me know. 

It's obviously not urgent. I'm just tinkering for the sake of exploration but it would be good to see what's failing here. 

Thanks

---

### Post by holiday on 2018-03-02
Just came upon this old post... 

The problem was that 17.10 Ubuntu moved on to systemd-networkd  and netplan so that /etc/network/interfaces was not being consulted. Once I moved my configuration to /etc/netplan and put 01-systemd-networkd.yaml in place, I had my static addresses. So  :

```
# /etc/netplan/01-systemd-networkd.yaml
network:
  version: 2
  ethernets:
    enp0s3:
      addresses: [192.168.1.124/24]
      gateway4: 192.168.1.254
      nameservers:
        addresses: [64.59.160.13]
    enp0s8: 
      addresses: [192.168.56.124/24]
```

 
And then :
```
 $ sudo netplan --debug generate
 $ sudo netplan --debug apply
```

I think I also had to 

```
$ sudo systemctl restart systemd-networkd
```

Or maybe even reboot. 

But anyway, that was the problem, and that was the solution, along with kicking Network Manager out of the house.

---

### Post by 3-joh8-x on 2018-03-02
I appreciate everyone who has attempted to fix the dns problems in 17.10. I have yet to find a real solution other than disabling everything except systemd-networkd and manually populating resolv.conf. It seems like every release of Ubuntu causes me to like it less. Can someone please get us back to a usable design? 

I run a local server with dnsmasq so that I can quickly bring up a VM and make it visible to the network. The servers all behave perfectly, but the Ubuntu Desktop with all the competing DNS management is really unusable.

---


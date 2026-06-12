---
title: "Samba and two network card"
date: 2015-09-16
forum: Server Platforms
---

### Post by zzixxus on 2015-09-16
Hello :)
I have a very difficult problem. In my school I want to install ubuntu server with samba to controle windows xp and 7 Domain (DC) but this server had 2 network card (eth0 and eth1). Windows computer doesn't have internet but server has it.
Server network configuration ( /etc/network/interfaces):

```

auto eth0
iface eth0 inet static
address 10.0.0.83
netmask 255.255.255.0
network 10.0.0.0
broadcast 10.0.0.255
gateway 10.0.0.1

auto eth1
iface eth1 inet static
address 192.168.0.100
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
dns-nameservers 192.168.0.100 8.8.8.8
dns-search mydomain.lan



```

Eth1 is the Samba domain controller and now need to connect the windows to eth1 card and access to a network from eth0

Thank You :)

---

### Post by darkod on 2015-09-16
Usually you have a gateway only on one interface. In most cases the interface that is going out to internet. In your case, is that eth0 or eth1? How is the server connected to the internet?

---

### Post by zzixxus on 2015-09-17
Hello, thank you for reply :)
My server connect (eth0) to router and network it works but my second card (eth1) is connected to switch in which windows computer are connect.

/etc/network/interface

```
root@DC01:/home/serv# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
broadcast 192.168.1.255
dns-nameservers 8.8.8.8 8.8.4.4
gateway 192.168.1.1


auto eth1
iface eth1 inet static
address 10.0.0.2
netmask 255.255.255.0
network 10.0.0.0
broadcast 10.0.0.255
gateway 10.0.0.1
dns-nameservers 10.0.0.2
dns-search mydomain.lan


```

/etc/sysctl.conf

```

# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1


```

/usr/local/samba/etc/smb.conf

```
root@DC01:/home/serv# cat /usr/local/samba/etc/smb.conf
# Global parameters
[global]
    workgroup = MYDOMAIN
    realm = mydomain.lan
    netbios name = DC01
    server role = active directory domain controller
    dns forwarder = 8.8.8.8 192.168.1.2

[netlogon]
    path = /usr/local/samba/var/locks/sysvol/mydomain.lan/scripts
    read only = No

[sysvol]
    path = /usr/local/samba/var/locks/sysvol
    read only = No

[Users]
directory_mode: parameter = 0700
read only = no
path = /Users
csc policy = documents


```

cat /etc/hostname 
DC01.mydomain.lan

/etc/hosts
```
root@DC01:/home/serv# cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    MYDOMAIN
127.0.0.1       localhost.localdomain            
10.0.0.2   DC01.mydomain.lan


```

What is wrong?

---

### Post by darkod on 2015-09-17
Why do you think something is wrong? What exactly does not work as you expect?

Is it a requirement for the server to be a gateway for the workstations? You can simply connect the router to the switch and have both the server and the workstations in the 192.168.1.x network. It will simplify the setup.
If you want the server to be gateway for the workstations, you also need basic iptables rule for masquerade. Only enabling ip forward in /etc/sysctl.conf is not enough.

Also, why is the server networking set up like that? What is the gateway 10.0.0.1? Your router is the gateway for the server. For eth1 on the server make it only:
```
auto eth1
iface eth1 inet static
   address 10.0.0.1
   netmask 255.255.255.0
```

That's enough. You can make the IP to be 10.0.0.2 if you prefer it instead of 10.0.0.1.

Also, what will serve as dhcp server for the workstations? Do they need to receive IPs automatically or all of them will have manual setup?

To enable forwarding on the server make a file called /etc/iptables.rules with this content:
```
*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]

COMMIT

*nat
:POSTROUTING ACCEPT [0:0]

-A POSTROUTING -o eth0 -s 10.0.0.0/24 -j MASQUERADE

COMMIT
```

That will make basic NAT rule for forwarding traffic. You can load these iptables rules by adding this line to /etc/network/interfaces for eth0, below gateway 192.168.1.1:
```
   post-up iptables-restore < /etc/iptables.rules
```

That will load them on each boot. Reboot the server after this changes and test ping 8.8.8.8 from the workstations.

---


---
title: "my domain settings"
date: 2006-08-22
forum: Server Platforms
---

### Post by tandre75 on 2006-08-22
Hello,

I am trying configure DNS for a LAN-only domain.  However, when I use the command *hostname -f*, I get *localhost*.  I want it to say "ubsrv3.lm.local," and the documentation for the postfix mailserver, says that it should not say anything like "localhost". 

I have 
1.  changed the file /etc/resolv.conf:
cat /etc/resolv.conf
[I]nameserver 127.0.0.1
nameserver 192.168.213.2
nameserver 192.168.1.222
domain lm.local
[/I]
 
2.  configured bind9 to serve DNS queries to other computers, without any errors

3.  and changed the file /etc/networking/interfaces:
[I]cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.43.136
netmask 255.255.255.0
gateway 192.168.43.2[/I]   

Is there supposed to be any other file that I have to look at?

I have also included some screenshots of my GUI network settings, if that can help anyone.

---


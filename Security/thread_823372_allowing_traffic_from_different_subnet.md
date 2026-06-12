---
title: "allowing traffic from different subnet"
date: 2008-06-09
forum: Security
---

### Post by amai on 2008-06-09
HOw to allow traffic from a different subnet to access Ubuntu server.

Here is my setup

PC-configuration
192.168.1.10
255.255.255.0
||
||
192.168.1.0
255.255.255.0
Firewall Machine-configuration( Firewall Machine have got two NIC's)
192.168.2.1
255.255.255.0
||
||
Ubuntu Server-configuration
192.168.2.2
255.255.255.0

********************

So traffic from LAN(GREEN)192.168.1.10 going to Ubuntu Server(DMZ)192.168.2.2) is passing through the firewall.
How to enable ubuntu to accept traffic from the local LAN which is on a different subnet.

PC to Firewall works fine
Firewall to Ubuntu works fine.
PROBLEM IS PC to UBUNTU connection

---

### Post by The Cog on 2008-06-09
Several things need to be checked for this to work.

Firewalling:
If the PC is running a firewall, this must allow connections to the server.
The firewall must allow connections to the server (and replies back of course).
If the Ubuntu server is running a firewall, that must allow conections from the PC.

Routing:
The PC must have a route to the server's network in its routing table, pointing to the firewall as the nect hop.
The Ubuntu server must have a route to the PC's network in its routing table, pointing to the firewall as the nect hop.

I guess you have thought of the firewall issues, so I guess you are probably missing a route. On Ubuntu you can check the routing table with the command:
**route**
and you should either see a default route or 192.168.1.0 with 192.168.2.1 as the next hop. If not, this command will add a default route to the firewall:
**sudo route add default gw 192.168.2.1**
You will need to make the gateway set at bootup. Best place to put it is as an up clause in /etc/network/interfaces - here is an example:
```
iface eth0 inet static
address 192.168.2.2
netmask 255.255.255.0
gateway 192.168.2.1
auto eth0
```

You need to make sure the PC has a return route too. On windows, I thnk **route print** should show you the routing table. I don't know where the default gateway is configured, offhand.

---

### Post by amai on 2008-06-11
thanks worked problem solved... You LEGEND

---


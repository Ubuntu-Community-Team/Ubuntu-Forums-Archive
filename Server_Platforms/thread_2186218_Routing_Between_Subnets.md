---
title: "Routing Between Subnets"
date: 2013-11-06
forum: Server Platforms
---

### Post by nicholas.b.cpp on 2013-11-06
I am running a dhcp server with two subnets:

10.0.0.0 = Physicaly connected clients
10.1.0.0 = VPN connected clients

I want both subnets to be isolated form each other but I would like to allow clients on one subnet to reach a client on the other subnet.

Ex:
Clients on subnet 10.1.0.0 accessing a FTP server running on subnet 10.0.0.0 at 10.0.3.4

How do I allow this in both iptables and the routing table

---

### Post by koenn on 2013-11-06
The simple answer is that you turn routing on on your server, and that's it.
[http://askubuntu.com/questions/95354/how-to-enable-forwarding-of-data-between-two-local-interfaces](http://askubuntu.com/questions/95354/how-to-enable-forwarding-of-data-between-two-local-interfaces)

if you need to add additional routes to the routing table, you use a command like ```
 route add {-host|-net} Target  [gw Gw]     [netmask N]   [[dev] If] 
```


iptables is a firewall : it"s meant to block traffic, not enable it. So normally you don't need it for routing, except in exceptional circumstances, eg if  you need NAT to get something to work, but that shouldn't be the rule.


The long answer is that the short answer assumes you have a router in each subnet,  i.e. that your server (which you are using as a routerà has an interface in each subnet. Whether that is the case is not mentioned in the question. Also, routing is all about subnets and their boundaries, so it's impossible to discuss it without knowing what the netmasks are. 
if I assume that your using an 8 bit netmask on your 10.0.0.0 network,  all your clients (including the 10.1.0.0 range) are on the same net and you don't need routing. If I assume a 24 bit netmask, your statement that  "the FTP server at 10.0.3.4 is on subnet 10.0.0.0" is wrong.  

If you don't understand the long answer or can't explain your network layout better than you did,  there's no way of knowing  what to put in the routing table.

---

### Post by nicholas.b.cpp on 2013-11-06
My bad for not giving more information about my networking setup

Subnet 10.0.0.0 use a netmask of 255.255.252.0 and subnet 10.1.0.0 use a netmask 255.255.248.0 
The server is acting as a router for the two subnets so routing is turned on already.

Unfortunately I am not that knowledge on networking engineering so I do not know how to setup the routes.

---

### Post by koenn on 2013-11-06
post your routing table while I have a look at your network numbers

edit : also give the ip-add/mask for your server's network interfaces, eg as in /etc/network/interfaces

---

### Post by dr1134 on 2013-11-06
So I messed up with my SSO account but got back my original account so that is what is up with the name change.

My network setup is as follows:

eth0
Interface to outside network
In case I did not mention this the server is running as the default gateway

eth1
IP = 10.0.0.1
Netmask = 255.255.252.0
Broadcast = 10.0.3.255

tun0
IP = 10.1.0.1
Netmask = 255.255.248.0
Broadcast 10.1.7.255

Routing Table:

[TABLE="width: 500"]
[TR]
[TD]Destination[/TD]
[TD]Gateway[/TD]
[TD]Genmask[/TD]
[TD]Flags[/TD]
[TD]Metric[/TD]
[TD]Ref[/TD]
[TD]Use[/TD]
[TD]Iface[/TD]
[/TR]
[TR]
[TD]0.0.0.0[/TD]
[TD]71.0.31.129[/TD]
[TD]0.0.0.0[/TD]
[TD]UG[/TD]
[TD]0[/TD]
[TD]0[/TD]
[TD]0[/TD]
[TD]eth0[/TD]
[/TR]
[TR]
[TD]10.0.0.0[/TD]
[TD]0.0.0.0[/TD]
[TD]255.255.252[/TD]
[TD]U[/TD]
[TD]0[/TD]
[TD]0[/TD]
[TD]0[/TD]
[TD]eth1[/TD]
[/TR]
[TR]
[TD]71.0.31.128[/TD]
[TD]0.0.0.0[/TD]
[TD]255.255.25.128[/TD]
[TD]U[/TD]
[TD]0[/TD]
[TD]0[/TD]
[TD]0[/TD]
[TD]eth0[/TD]
[/TR]
[/TABLE]

Routing for tun0 has not been add due to the fact that VPN has not been full setup but I am confident that I can add this plus it should be done automaticaly

---

### Post by koenn on 2013-11-06
> **dr1134 said:**
> 

Routing for tun0 has not been add due to the fact that VPN has not been full setup but I am confident that I can add this plus it should be done automaticaly

You're going to need a line in the routing table that says 10.1.0.0/(mask) is at dev tun0
you can add that with something like```
 route add  -net 10.1.0.0  netmask 255.255.248.0  dev tun0   
``` 
but most likely you can trigger that from the OpenVPN config so that the route is added when the tun interface comes up

That's all you need, routing wise -- if you're running iptables you may need to add ALLOW rules, that depends on how yout firewall is setup.



(it's bed time here, so I'm off)

---

### Post by dr1134 on 2013-11-06
Thanks for all the help so far

I add the iptables and the routing rules for tun0

Now to get users on the vpn subnet able to talk to the ftp server would I do the following

```

[COLOR=#000000][FONT=Ubuntu Mono]route add  -net [/FONT][/COLOR][COLOR=#000000]10.0.3.4[/COLOR][COLOR=#000000][FONT=Ubuntu Mono] netmask 255.255.252.0  dev tun0[/FONT][/COLOR]

```

---


---
title: "Openvpn Iptables Protection"
date: 2013-02-01
forum: Security
---

### Post by jamrop on 2013-02-01
Hey

I have ubuntu as a vpn gateway for my local network

My openvpn uses tap interface

I am worried that if i lose my openvpn connection, my local network (eth0) will be wild open

I was wondering if i am missing something in iptables to secure it more, for example if i lose my openvpn, to stop my local network accessing the internet, or if there is something else i can do? reconnect?

Also, is there anything else not in my iptables to make it more secure from attacks hacks etc?

It gets a bit confusing with Forwards and Output for me lol. Still trying to learn it.

Many many thanks

Below is my iptables list

FORWARDS
Code:

```
iptables -t nat -A POSTROUTING -o tap0 -j MASQUERADE
iptables -A FORWARD -i eth0 -o tap0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i tap0 -p tcp --dport 0:65535 --sport 53 -j ACCEPT
iptables -A FORWARD -i tap0 -p udp --dport 0:65535 --sport 53 -j ACCEPT
iptables -A FORWARD -i tap0 -p tcp -m tcp --sport 80 -j ACCEPT 
iptables -A FORWARD -i tap0 -p tcp -m tcp --sport 443 -j ACCEPT 
iptables -I FORWARD -p tcp --dport 1194 -j ACCEPT
iptables -I FORWARD -p udp --dport 1194 -j ACCEPT
iptables -A FORWARD  -p tcp -m tcp --sport 6667 -j ACCEPT 
iptables -A FORWARD  -p tcp -m tcp --sport 6697 -j ACCEPT 
iptables -A FORWARD  -p tcp -m tcp --sport 9050 -j ACCEPT
iptables -A FORWARD  -p tcp -m tcp --dport 9050 -j ACCEPT
iptables -A FORWARD -i tap0 -j DROP
```


OUTPUTS


```
iptables -A OUTPUT  -p tcp -m tcp --dport 6667 -j ACCEPT 
iptables -A OUTPUT -o tap0 -p udp -m tcp --dport 133 -j ACCEPT 
iptables -A OUTPUT -o tap0 -p tcp -m tcp --dport 80  -j ACCEPT
iptables -A OUTPUT -o tap0 -p tcp --sport 0:65535 --dport 53 -j ACCEPT
iptables -A OUTPUT -o tap0 -p udp --sport 0:65535 --dport 53 -j ACCEPT
iptables -A OUTPUT -p icmp -o tap0 -j DROP
iptables -A OUTPUT -o tap0 -j DROP
```

INPUTS


```
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -d 127.0.0.0/8 ! -i lo -j REJECT --reject-with icmp-port-unreachable
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A INPUT -i eth0 -j ACCEPT
iptables -A INPUT -p icmp -m icmp --icmp-type 8 -j ACCEPT
iptables -A INPUT -m limit --limit 5/min -j LOG --log-prefix "iptables denied: " --log-level 7
iptables -A INPUT -i eth0 -p tcp  --dport 22 -j ACCEPT
iptables -A INPUT -j REJECT --reject-with icmp-port-unreachable
iptables -A INPUT -i tap0 -j DROP
```

---

### Post by bodhi.zazen on 2013-02-01
The only thing I noticed is that you are accepting all traffic on eth0

> iptables -A INPUT -i eth0 -j ACCEPT

so yes, eth0 looks as if it is accepting all traffic.

---

### Post by jamrop on 2013-02-01
hey

thanks for noticing, is there anything i can do to make it more secure? does that mean, the outside internet can have access to all my devices on the local network?

If i stop inputs on etho , does that not stop all my services, e.g. dns, http, squid, internet sharing, from working ?

---

### Post by bodhi.zazen on 2013-02-01
> **jamrop said:**
> hey

thanks for noticing, is there anything i can do to make it more secure? does that mean, the outside internet can have access to all my devices on the local network?

If i stop inputs on etho , does that not stop all my services, e.g. dns, http, squid, internet sharing, from working ?

There are 2 types of services, public and private.

Iptables is not the best tool for public servers, unless you want to rate limit connections.

Example - web servers. You will have to allow port 80.

Private - Example ssh. Here you can allow only a range of access.

Also, if you do not have an open port, there is noting to firewall.

So, if you are not running a web server, how is security increased by denying access to port 80 ?

---

### Post by jamrop on 2013-02-02
Hey

It is a private network.

eth0 is my local network. Tap0 is my access to the internet (openvpn)

When tap0 is up, does that mean that eth0 input is just for the local network?

If i lose my openvpn connection , tap0 will drop, meaning that eth0 will be my local and access to the internet. Meaning everything is wild open? as i have ```
iptables -A INPUT -i eth0 -j ACCEPT 
```

---

### Post by bodhi.zazen on 2013-02-02
Well there are sort of 2 ways of looking at what you are doing.

I assume your physical hardware is a router -> LAN -> and eth0 is on the LAN.

In that event, most routers serve as a (NAT) firewall.

When you use the VPN client, you bring up a virtual interface, tap0.

The VPN connection encrypts and tunnels the traffic to the VPN server.

The physical layer is still the same, packets enter and leave both the eth0 and your router. With VPN the go to the VPN server, without VPN they to to the wild.

So I am guessing you want to configure your router.

What services are you running on the client that you need to firewall ?

---

### Post by jamrop on 2013-02-02
hey

I have a vpn gateway

I have router(dhcp disabled) - vpn gateway (ubuntu server dhcp (with the firewall rules listed below)) -- lan

So my devices all connect to my vpn gateway

> What services are you running on the client that you need to firewall ? 

I want to protect my local network from hacks etc, and if my vpn server goes down, to disable internet access or to restrict with iptables

---

### Post by jamrop on 2013-02-03
hey

On a side note, my router has dd-wrt, so maybe able to edit iptables on that to stop everything when my openvpn goes down? 

many thanks

---


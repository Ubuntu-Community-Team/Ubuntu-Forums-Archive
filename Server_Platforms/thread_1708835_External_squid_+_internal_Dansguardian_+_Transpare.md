---
title: "External squid + internal Dansguardian + Transparent proxy... fail..."
date: 2011-03-17
forum: Server Platforms
---

### Post by Nessaja on 2011-03-17
Hi,

I've search everywhere for an answer but I can't seem to figure this out.

I have a gateway server that handles internet connectivity on eth0 (192.168.0.1)
The rest of the network is connected to eth1 (192.168.1.1)

And then on the network I have another Linux system 192.168.1.2 that I use with squid.

now,

On the gateway server I've got dansguardian that listens on port 3128 and on the other Linux system connected to eth1 I've got squid that listens to port 3129. Dansguardian is set up to send all packets to 192.168.1.2 port 3129.
Also on the gateway server I've got iptables set up with this commands:
```

iptables -t nat -A PREROUTING -i $INTERNET -p tcp --dport 80 -j REDIRECT --to-port $SQUID_PORT

iptables -t nat -A PREROUTING -i $LAN_IN -p tcp -s 192.168.1.108 --dport 80 -j DNAT --to $SQUID_SERVER:$SQUID_PORT


```Please note that 192.168.1.108 is my testing system.

With this setup everything runs 100%
But, If I change
```
iptables -t nat -A PREROUTING -i $LAN_IN -p tcp -s 192.168.1.108 --dport 80 -j DNAT --to $SQUID_SERVER:$SQUID_PORT

```to
```
iptables -t nat -A PREROUTING -i $LAN_IN -p tcp --dport 80 -j DNAT --to $SQUID_SERVER:$SQUID_PORT

```I get this message in internet explorer:
```

* Unable to forward this request at this time. 

This request could not be forwarded to the origin server or to any parent caches. The most likely cause for this error is that:

    * The cache administrator does not allow this cache to make direct connections to origin servers, and
    * All configured parent caches are currently unreachable. 

Your cache administrator is root. 

```Has anybody ever had this error with a similar setup?

To answer 1 question: I do not want to install squid on the gateway system, I'm running it in a virtual PC to increase speed of backup/recovery and deployment in other branches....

EDIT:
Tried iptables -t nat -A PREROUTING -i $LAN_IN -s 192.168.1.0/24 -p tcp --dport 80 -j DNAT --to $SQUID_SERVER:$SQUID_PORT

Also gave the same results...

---


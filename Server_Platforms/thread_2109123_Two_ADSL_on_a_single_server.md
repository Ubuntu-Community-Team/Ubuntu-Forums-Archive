---
title: "Two ADSL on a single server"
date: 2013-01-26
forum: Server Platforms
---

### Post by allanarab on 2013-01-26
This is the topology of my network ...

1 server "Squid Cache" and filter content.
This server has 4 network cards

eth0 -> ADSL1
eth1 -> ADSL2
eth2 -> Network 192.168.10.0/24
eth3 -> Network 192.168.20.0/24


The two are the same ADSL provider, what I need is to have both active and direct ADSL connection as follows:

eth0 (ppp0) <-> eth2
eth1 (PPP1) <-> eth2

I'm not able to make this direction. Can activate both ADSL, I can browse the server, but the network can not.

Note: before they spring talk "looks iptables rules" ... below this part of them ..

# Sharing
iptables-t nat-A POSTROUTING-o ppp0-j MASQUERADE (here I am ppp0 only with the active, because the network can not stop)

# Squid Proxy (and the two networks are using the same link)
iptables-t nat-A PREROUTING-i eth2-p tcp - dport 80-j REDIRECT - to-port 3128
iptables-t nat-A PREROUTING-i eth3-p tcp - dport 80-j REDIRECT - to-port 3128


ja follow this article (in Portuguese) but failed (remade 2 times): [http://www.vivaolinux.com.br/artigo/Configurando-2-%](http://www.vivaolinux.com.br/artigo/Configurando-2-%) 28dois% 29-ADSL-links-in-same-server


Note2: No, the two networks can not share the same ADSL and do not "balance" because of the two networks are separate companies.


Who can help me I am grateful.

---

### Post by darkod on 2013-01-26
Did you activate the forwarding in /etc/sysctl.conf? There is an entry for IPv4 like:
#net.ipv4.forward=1

You need to uncomment it, remove the # symbol in front. Save and close the file. This is needed so that the machine can forward traffic between its interfaces.

Also, in the POSTROUTING iptables rule I'm not sure if it needs to be -o eth0 or -o ppp0. I would try with eth0 since that is the interface on the server, it doesn't matter that it has ppp connection configured on it. But I'm not sure about this.

How are you calling the iptables rules on boot, are they in a file that you use, or what?

And what are the iptables policies for the INPUT, FORWARD and OUTPUT chains?

EDIT PS: Also, I'm not sure if you can use multiple gateways. If you can setup only one gateway, it doesn't matter if you have one or more ADSL connections configured. You might think about getting some dual WAN router that will automatically use the second ADSL if one fails. Most of them can do load balancing if you want to use it.

---


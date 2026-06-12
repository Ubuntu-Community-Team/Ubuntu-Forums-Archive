---
title: "help with IPTABLES"
date: 2010-05-09
forum: Security
---

### Post by turbochad on 2010-05-09
I've currently studying a network engineering diploma. I'm now in my final session on the final project.

I have a experience in Cisco routing but am having problems with IP tables.

Here is the flow diagram.

[http://i180.photobucket.com/albums/x42/chadchook/ChadFlow.jpg](http://i180.photobucket.com/albums/x42/chadchook/ChadFlow.jpg)

What i need to do is set up the rules to deny everything then just allow what i want throught.

Rules.

##FLUSH it

sudo iptables -F
sudo iptables -t nat -F


##Change the Default Policys

sudo iptables -P INPUT DROP
sudo iptables -P FORWARD DROP
sudo iptables -P OUTPUT DROP


## NAT.

sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
sudo iptables -A FORWARD -i eth0 -o eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT
sudo iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT

## allow established connections back through input

sudo iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

## allow input from loopback

iptables -A INPUT -i lo -j ACCEPT

## allow outbound http proxy

sudo iptables -A OUTPUT -p tcp --dport 8080 -o eth0 -j ACCEPT





However the problem im having is after im NATing everything is let through dispite. Any help would be great

i presume the line

sudo iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT

is where things everything is let through. However my problem is somewhat larger than that as i would to only allow for some protocols through.

Does this mean that i would have to forward each protocol i wont through, leaving the others not specificed to be denyed.

or is there

can you filter protocols eg port 8080 by simply

sudo iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT
sudo iptables -A OUTPUT -p tcp --dport 8080 -o eth0 -j DROP

---

### Post by DGortze380 on 2010-05-11
> **turbochad said:**
> 
However the problem im having is after im NATing everything is let through dispite. Any help would be great

i presume the line

sudo iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT

is where things everything is let through. However my problem is somewhat larger than that as i would to only allow for some protocols through.

Does this mean that i would have to forward each protocol i wont through, leaving the others not specificed to be denyed.

or is there

can you filter protocols eg port 8080 by simply

sudo iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT
sudo iptables -A OUTPUT -p tcp --dport 8080 -o eth0 -j DROP

This is a little convoluted. Are you talking about egress filtering?

Yes, if you're using an implicit deny, you need to specify which ports and protocols to allow.

---


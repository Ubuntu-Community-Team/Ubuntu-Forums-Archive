---
title: "Iptables forwarding between vlans?"
date: 2009-02-07
forum: Server Platforms
---

### Post by Don6 on 2009-02-07
I work at a computer repair shop, and we have two vlans. One is for client machines, the other is for our private shops ones, to prevent infections spreading to our desktops and Windows servers. This is done on a Cisco Catalyst switch.

We then have a server running Ubuntu server with Samba, that is in both vlans, to provide a way to share files between them, without the risk of passing on a virus (autorun.inf has been made in the shares, then chowned to root).

What I'm wishing to do is port forward port 80 on the linux server, so that computers in the client vlan can access our database sever, which is in the private vlan.

I've tried various iptables port forwarding rules, such as the one below, but none of them work. They all seem to be for computers that have private and public addresses, with multiple network cards, whereas our server is only on the private network, and has just one network card, eth0. For reference, the ips are in the 192.168.0.0/24 range.
```
iptables -t nat -A PREROUTING -p tcp --dport 80 -j DNAT --to 192.168.0.11:80 
iptables -A FORWARD -s 192.168.0.11 -p tcp --dport 80 -j ACCEPT
```
When this code is used, the port shows up as `filtered` on an nmap scan, and a connection can't be made through.

Can anyone offer any advice?

-Don6

---

### Post by Don6 on 2009-02-11
No one?

---

### Post by Adina on 2009-02-11
I am by no means a network expert and I might be wrong, but I'm pretty sure that if you want to forward a packet from one network to another then you will need 2 nics.

---

### Post by Fire_Chief on 2009-02-11
So do both VLANs have the same IP range on them?

---

### Post by Don6 on 2009-02-11
Yeah, both are in the 192.168.0.0/24 range.

---

### Post by digitalbenji on 2009-02-11
do both networks have the same gateway?

---

### Post by Fire_Chief on 2009-02-11
That won't work when trying to pass traffic between the two networks since each network thinks the other vlan is local. What I mean by that is if both vlans are using the same IPs then a client in one VLAN would not know to communicate through the ubuntu box to get to the other VLAN. It would instead try to connect directly to the destination address.

You need to use two different IP subnets for your VLANs. This would allow proper routing between them when desired and configured.

Cheers!

---

### Post by digitalbenji on 2009-02-11
yeah that was what I was getting at by asking if they had the same gateways.  I think if you set the gateways for the 2 networks to be different, you may be able to do this using some clever iptables rules, but it will be much more easy to configure if you have two distinct subnets.

---

### Post by Don6 on 2009-02-12
Ok, I'll have to look at subnetting them. Thanks for the advice.

~Don6

---

### Post by _Dan on 2009-02-12
Sorry to butt in, but would you mind telling me how to get PREROUTING working for iptables? I haven't been able to...

I posted about it here: [http://ubuntuforums.org/showthread.php?t=1066767](http://ubuntuforums.org/showthread.php?t=1066767)

---


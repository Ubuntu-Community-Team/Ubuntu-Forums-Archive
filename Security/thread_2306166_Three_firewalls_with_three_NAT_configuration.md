---
title: "Three firewalls with three NAT configuration"
date: 2015-12-12
forum: Security
---

### Post by HardTrickySecurity on 2015-12-12
I am not shure if what I am trying to do is even possible, I want to connect to the internet using 3 firewalls and the 3 of them using NAT. Its for educational purposes.
I have a cisco ccna certification and I play around with linux a lot so I know a little bit about this stuff but I never seriously tried to make this setup to work.
I already have all the hardware neccesary I just need to configure it. I have a Cisco PIX 515E firewall and that one its already configured, is working fine.
But now I need to add a second firewall using Alpine Linux OS and I need to configure NAT on this one using iptables wich is supported.

So the topology will be like this, using NAT in the 3 firewalls and as you can see I am confused on how that will even work because of the public and private IPs in the interfaces of the second and third firewall:

Internet (ISP WAN) ---> (DHCP public ip) Cisco PIX firewall (Private IP) ---> (Private IP?)  Alpine Linux firewall (Private IP?) ---> (Private IP?) My PC Lubuntu firewall (Private IP?)

or

Internet (ISP WAN) -- > (DHCP public ip) Alpine Linux firewall (Private IP) ---> (Private IP?) Cisco PIX firewall (Private IP?) --> (Private IP?) My PC Lubuntu firewall (Private IP?)

So the OS topology will be:

ISP WAN ----> Cisco OS ----> linux iptables -----> linux iptables ----> My PC LAN

or

ISP WAN ----> linux iptables ----> Cisco OS -----> linux iptables ----> My PC LAN

So first, is this possible? If is possible how can I do that in a simple and easy way. If its not possible well at least I will try just Alpine linux firewall alone.

The configuration on the 3 firewalls should be the same:

- Allow all outgoing traffic
- Block all incoming traffic
- Block all incoming icmp (ping and so on)

- And finally use NAT:

Public and private interface.
Public and private ip.
External public network and internal private network.

Links:

[http://www.revsys.com/writings/quicktips/nat.html](http://www.revsys.com/writings/quicktips/nat.html)
[http://brianckelley.com/2015/02/simple-easy-nat-port-forwarding-for-iptables-ubuntu/](http://brianckelley.com/2015/02/simple-easy-nat-port-forwarding-for-iptables-ubuntu/)
[https://www.howtoforge.com/nat_iptables](https://www.howtoforge.com/nat_iptables)
[https://www.debian-administration.org/article/23/Setting_up_a_simple_Debian_gateway](https://www.debian-administration.org/article/23/Setting_up_a_simple_Debian_gateway)
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables#Static_NAT](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables#Static_NAT)

---

### Post by Doug S on 2015-12-13
> **HardTrickySecurity said:**
> So first, is this possible?Yes. and in whatever order you want.
> **HardTrickySecurity said:**
> If is possible how can I do that in a simple and easy way.Just treat each step by itself, and use a different local sub-net between each box.
I can not comment on the Cisco box, but the other two linux boxes should be fairly trivial, using the references you already provided.

---

### Post by HardTrickySecurity on 2015-12-16
I was able to implement NAT in Alpine Linux so I am using that one as a firewall. Looks like my technical problems went away with this new setup, but I need to test it a little bit more to be 100% sure.

My new setup:

ISP WAN -> Alpine Linux (NAT) -> My PC LAN Lubuntu 14 trusty stable

---


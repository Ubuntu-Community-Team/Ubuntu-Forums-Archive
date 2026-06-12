---
title: "Ubuntu Firewall Box: How to pass packets from Internal Interface to External Interfac"
date: 2012-08-03
forum: Server Platforms
---

### Post by duplex50 on 2012-08-03
Hello Again,

Everyone was extremely helpful on my last posts, so I am back again!

My Ubuntu 12 server has eth0 attached to dsl model and eth1 is attached to internal network via a switch. I can now successfully talk internally through eth1 and externally to the internet via eth0.

I would like to know how I can start using eth1 as the default gateway for clients on my network.

eth0 is configured as 192.168.254.2 and eth1 is configured as 192.168.1.23.

I assume that packets are passed from 192.168.1.0 network to 192.168.254.0 network via IPTABLES. I plan on using fwbuilder as my front-end for IPTABLES. Before I start using this front end, I would like to make simple IPTABLES entries via command line so I can point my workstation to 192.168.1.23 as the gateway and connect out to the internet. Once again, I just want to test connecting to the internet from my workstation (192.168.1.246) through eth1 on my server (192.168.1.23) out through eth0 (192.168.254.2) to the internet before implementing the front-end.

So:
Workstation (192.168.1.246) requesting [www.google.com]("http://www.google.com/") -->via--> Firewall eth1 (192.168.1.23) -->via--> eth0 (192.168.254.2) -->via--> DSL modem (192.168.254.254).

What do I have to do to access the internet from my workstation through the Firewall?

I also want to set this up manually without using front-end GUI for learning purposes as well. I want to understand what all is going on regarding the network setup.

Please let me now if any Output would assist.

Thank you all very much again!

---

### Post by darkod on 2012-08-03
First, you need to open /etc/sysctl.conf and uncomment (activate) the line saying something like:
net.ipv4.ip_forward = 1

Then you need to add one iptables outgoing rule, like:
sudo iptables -t nat -A POSTROUTING -o eth0 -s 192.168.1.0/24  -j MASQUERADE

If I got the spelling right, that should do it. Note that this iptables command is not permanent, after you reboot the ubuntu box it goes away. But this is the fast test you are looking for.

Basically that creates a rule in the nat table with eth0 as the outgoing interface, coming from the LAN network 192.168.1.0/24 doing a NAT masquerade.

See how it works.

---

### Post by duplex50 on 2012-08-03
Hi Darko,

Thanks again for your replies and expertise.
 
What is the purpose and use of sysctl.conf?
 
Does uncommenting the net.ipv4.ip_forward = 1 line in this file, just change security settings and ALLOW ipv4 traffic to be forwarded?
 
And does sudo iptables -t nat -A POSTROUTING -o eth0 -s 192.168.1.0/24 -j MASQUERADE CREATE that forward?

Once again, I am trying to understand as much about Linux networking/interfaces setup as I can.  I've learned quite a bit in the last few months and would like to absorb as much as possible.  I appreciate your answers.
 
 
Thanks again!

---

### Post by darkod on 2012-08-03
I don't know too much into details too, just the using the box as a gateway is achieved with that ip_forward = 1 and the masquerade using iptables. Of course, this assumes no firewall is blocking the OUTPUT or FORWARD chains. If you already activated a firewall, make sure it allows outgoing traffic.

---

### Post by duplex50 on 2012-08-03
I actually uninstalled fwbuilder and made sure that IPTABLES --list shows nothing.
 
So if I add these two commands, I will be able to set default gateway on my workstation to 192.168.1.23 (eth1 on Linux Firewall Server) and get out to the internet?

---

### Post by darkod on 2012-08-03
Yes, you should.

It's better to restart the server after changing sysctl.conf and run the iptables command after it boots up. Remember, it's not permanent. There is no need to restart after adding iptables rules.

---

### Post by SeijiSensei on 2012-08-03
By default, Ubuntu ships with net.ipv4.ip_forward=0 as a security precaution.  Changing the value to one permits packets to be forwarded between the machine's interfaces. 

To make the masquerading rule permanent, add it to /etc/rc.local.  That file is run at the end of the boot sequence.

---

### Post by Cheesemill on 2012-08-04
Pretty much the exact reply that you've already been given but with a bit more detail:

[http://codeghar.wordpress.com/2012/05/02/ubuntu-12-04-ipv4-nat-gateway-and-dhcp-server/](http://codeghar.wordpress.com/2012/05/02/ubuntu-12-04-ipv4-nat-gateway-and-dhcp-server/)

---

### Post by duplex50 on 2012-08-06
Hello Everyone,

Thank you all again for your instruction and expertise.  I was successfully able to forward traffic coming to and from my PC through my Firewall.  Now to create my rules.
 
Thank you again!

---


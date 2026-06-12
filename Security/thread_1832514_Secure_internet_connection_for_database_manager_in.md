---
title: "Secure internet connection for database manager in an apartment complexx"
date: 2011-08-24
forum: Security
---

### Post by erinod on 2011-08-24
Hi guys,
I  work with a database on a LAMP server and the development environment  that was set up for me is on a Kubuntu system so I've turned to this  forum for help in the past. But basically I have this scenario: I'm  managing a database on a server that is physically located in a  different town where my job's office is, but I do all my work from home  and I live in an apartment complex that pays for and provides me with a  Comcast internet connection. Since this database has sensitive company  information in it, I would like to take steps to make my internet  connection secure. 

I was told that having an internally assigned  ip address and connecting to the internet through a router is not very  secure and I assume means I am some how vulnerable to any techy  engineering students in my building? When I use any of those What's my  IP Address websites I can see that my external ip address is different  than the ip address my Mac tells me I have when I check under network  settings. My Mac network settings tells me my ethernet connections ip  address, the subnet mask, and the router address, and they are all  different numbers.

I have a VPN software running on my work laptop which I turn on anytime I'm doing work stuff.

My  questions are: (1) Does this VPN software provide me security so that  when I login to the database or access the company server, I'm not  exposing the company to undue risk?

(2) Am I correct in my assessment that I am connecting to the internet through a router?

(3) Are there other steps I should take to secure my internet connection and what are they?

                             [IMG]http://kubuntuforums.net/forums/Themes/classic/images/icons/modify_inline.gif[/IMG]

---

### Post by spynappels on 2011-08-25
Hi,

Your basic assumption that you are behind a router is correct. The question of whether you are at risk from others in the same building depends on how networking was set up by the building owners. There are things you can do to decrease your visibility and/or vulnerability, which I'll go in to in a minute.

However, for your initial question, if you are accessing your work network through a VPN, then that traffic is secure.

There are things you can do to check if you are on an openly shared network in your building. However, be aware that running some of these tests can be interpreted by some as an offensive act, so be aware of this. You could do a network scan to see what other computers you can see on the network and what services are running on them, although this second step is not strictly necessary. If you are on an open network, I'd suggest getting a small WAN router and using it as a firewall between you and the rest of the building.

some more info on your local IP address and subnet mask etc would be helpful to help confirm the networking status of your building. It would tell us whether they have enabled small subnets and VLAN, which would effectively segment the network into smaller, more secure individual "zones".

---

### Post by bodhi.zazen on 2011-08-25
> **erinod said:**
> Hi guys,
I  work with a database on a LAMP server and the development environment  that was set up for me is on a Kubuntu system so I've turned to this  forum for help in the past. But basically I have this scenario: I'm  managing a database on a server that is physically located in a  different town where my job's office is, but I do all my work from home  and I live in an apartment complex that pays for and provides me with a  Comcast internet connection. Since this database has sensitive company  information in it, I would like to take steps to make my internet  connection secure. 

I was told that having an internally assigned  ip address and connecting to the internet through a router is not very  secure and I assume means I am some how vulnerable to any techy  engineering students in my building? When I use any of those What's my  IP Address websites I can see that my external ip address is different  than the ip address my Mac tells me I have when I check under network  settings. My Mac network settings tells me my ethernet connections ip  address, the subnet mask, and the router address, and they are all  different numbers.

I have a VPN software running on my work laptop which I turn on anytime I'm doing work stuff.

My  questions are: (1) Does this VPN software provide me security so that  when I login to the database or access the company server, I'm not  exposing the company to undue risk?

(2) Am I correct in my assessment that I am connecting to the internet through a router?

(3) Are there other steps I should take to secure my internet connection and what are they?

                             [IMG]http://kubuntuforums.net/forums/Themes/classic/images/icons/modify_inline.gif[/IMG]

I respectfully disagree with most of what spynappels advised, there is no need to start scanning networks.

You basically need to do a few simple things.

1. Connect to your server over an encrypted connection. ssh, VPN, FreeNX are all fine.

For what you are doing, ssh is probably sufficient, if you need to forward web apps or the database, use port forwarding. If you need graphical applications , use ssh -X

2. Secure the database and web server. By default, most database severs will listen on localhost only. You can configure apache to do the same.

If it is a public server (you are forwarding posts outside the LAN), then you so not need to worry about the LAN.

If it is a private server, use iptables.

iptables -A INPUT -s your_ip -j ACCEPT
iptables -A input -s your_lan_with_netmask -j RDOP

For example

iptables -A input -s 192.168.0.0/16 -j DROP

---

### Post by spynappels on 2011-08-25
I probably should clarify what I said a little:

I meant that for connecting to his work, the existing VPN will more than likely suffice. 

For the general question of whether his computer was at risk from technologically aware people elsewhere the building, and in the absence of information from the building's management on network topology, the other things I suggested are one way of getting information, and securing his computer if the information gleaned is less than reassuring.

---


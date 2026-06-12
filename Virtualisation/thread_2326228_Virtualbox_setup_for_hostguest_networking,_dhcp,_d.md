---
title: "Virtualbox setup for host/guest networking, dhcp, dns, and webserver"
date: 2016-05-29
forum: Virtualisation
---

### Post by scott133 on 2016-05-29
Hello all,

I am working on a project for someone else that includes some method of virtualization. The preference was linux so since I have some experience with linux and ubuntu such as running muck servers on them and minetest servers.

I am using a laptop and I have it setup so far but I am having a tough time setting up a virtual server to use ubuntu server 16.06 as a router on one virtual machine that routes to another virtual server that has to be in a seperate network from the both the host and the first virtual machine. I´ll break this down.

The project: Using a virtualization program, I want to create two virtual machines and have them each on their own network. The first machine, I want to have dns, dhcp, firewall, and port forwarding. The second machine I want to have it be a web server. I need to have an external computer be able to access the host, then go through the first network to get to the first virtual machine and have it do dns and dhcp for the internal network that it passed to to the second virtual machine and access a service on the second machine.

I have selected virtualbox to be the virtualization software. I´ve been researching a ton on virtualbox and reading about the setup. I´ve used it a little bit before. I have everything pretty much setup. Getting there wasn´t easy. Where to start?

vmserver1 is the name of the host for the two virtual server. vm1 is what I have named the first server, that is the server that is supposed to be the dhcp, dns, firewall, and port forwarding server for the network that the second server, called vm2 is on. vm2 is the server that has apache webserver installed.

vm1 is setup currently as a host only network. I´ve had vm2 set on an internal network.

vm1 has two networking adapters enp0s3 and enp0s8, one is for the host only network vboxnet0, the second one is for the internal network vnet1. I have the interface for the internal network setup as a static server.

So, the webserver seems to work well, if I set it up to connect just  directly to the host without going through the first virtual machine  (ubuntu server router) I can bring it up fine, but when I try to connect  through the first virtual server, it doesn´t work. Naturally, it  doesn´t have a route so it shouldn´t be able to.

vm2 has one networking adapter set on the vnet1 network. It receives dchp assignment ok from vm1. The dns is working fine from vm1. I didn´t set it up any further other than the A record to point to the webserver which the dhcp server assigns a fixed address ok with its mac address. So, when I use curl on the domain name I chose, it was pulling up the webpage from vm2.

I can bring up the webpage using curl from vm1.

I have webmin installed on vmserver1, vm1, and vm2 and I can access vm1s webmin. Then through that I can access vm2´s webmin. Cool. I wish I could stop there but I want to access the apache webserver but it can´t which is again, probably because of the routing. that has me stumped.

Ok, so the ways I´ve tried to route it is through iptables, setting it to pass from the forward facing interface to the internal network interface. I cleared out the tables, redid it again and again but can´t seem to get anything from the host to vm2.

Alright. Now, I got stumped with it so I figured I´ll set it up another way to just pass internet from the host network to vm1 to vm2, essentially retuning vm1 as an ubuntu server router. I used bridge-utils. I had vm1 set to vboxnet0 (that has a network ip address of 10.10.10.x) and bridged it (made a br0 interface with dhcp) with the hosts wired port and wireless card. Then I installed bridge-utils and bridged (setup a br0 interface) on vm1 and  bridged the forward facing port with the internal facing port. Then on vm2, I can ping [www.google.com]("http://www.google.com"). Yay! but I can´t get a ping in from the host to vm2. I tried to get the webpage, but nothing.

I´ll look at the iptables and maybe clear them to see if I can get connection back. But it doesn´t make any sense to me why setting up the ip tables didn´t do this before I setup the bridge ports. Maybe from the host from the external (to the host) internet modem/router. 

I mean, before I bridged the interfaces I tried to setup a bridged connection in virtualbox network setting (where it wasn´t host only network) to bridge directly to the host computer´s internet port.

Any help would be appreciated. I´ve been trying to set this up for about five days now. I just today did the routing of the internet to the second virtual machine.

Thank you for your help and input. I have many configuration points so I didn´t know which pictures would be helpful to post but if you want a screenshot of anything, please let me know.

---

### Post by houstonbofh on 2016-05-30
You do not have a route on your laptop to the machine beyond the virtual router in your environment.  So no way to see webmin.

---

### Post by scott133 on 2016-05-31
Yes, now it does not. But, before I was able to get to webmin on the second vm (vm2) that is on the internal network. Of course it may be to do with the fact that the local network doesn't have a default gateway with the router and when I set it up with a default gateway before that it could see the webmin on vm2. Then, when I did a broadcast for webmin servers it picked it up. Now, it actually can pick it up now with the current setup if I piggy back on the hosts webmin to the vm1s webmin and it can see the server for the webmin on vm2, but trying to connect to it now just results in it loading. It was able to connect to it before with similar iptables rules. I couldn't connect to it directly with an ip address but through the webmin into the webmin into the webmin. Perhaps that means I need to open port 80 on vm2. on vm1 it was set to forward 80 from one port to another. I am going back and writing all of this stuff down. It is hard for me to organize it all together to say what is happening.

---

### Post by MAFoElffen on 2016-06-01
Have you thought about adding a "route rule" as a default hop or a formal VM bridge? (search on virtual network bridge to host network... or ask about it)

---


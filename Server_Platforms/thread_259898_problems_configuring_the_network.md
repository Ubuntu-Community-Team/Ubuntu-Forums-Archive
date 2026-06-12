---
title: "problems configuring the network"
date: 2006-09-18
forum: Server Platforms
---

### Post by charles.g.moore on 2006-09-18
Hey guys I am so lost, I am trying to follow this how-to
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3)

but I dont understand the part about setting up my network

I have one of those dydns dynamic addys it's charlesgmoore.homelinux.com
my address according to dydns is 24.253.31.187
and the servers address behind the wireless router at home is 192.168.1.102
I dont know what to put in my /etc/network/interfaces this is what i have now...

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

And if i ping charlesgmoore.homelinux.com from my desktop pc i get:
64 bytes from ip24-253-31-187.lv.lv.cox.net (24.253.31.187): icmp_seq=1 ttl=64 time=1.19 ms
64 bytes from ip24-253-31-187.lv.lv.cox.net (24.253.31.187): icmp_seq=2 ttl=64 time=0.996 ms

---

### Post by Jussi Kukkonen on 2006-09-18
> I have one of those dydns dynamic addys it's charlesgmoore.homelinux.com
my address according to dydns is 24.253.31.187
and the servers address behind the wireless router at home is 192.168.1.102
I dont know what to put in my /etc/network/interfaces this is what i have now...

Please describe the network you wish to have in more detail: how many machines, are they behind the same router, which machines need to be accessible from outside the router, etc. 

Also describe what you have working already and what is missing -- it looks like you have at least the desktop machine somehow connected, and dyndns working, but it's hard to tell what the problem is...

---

### Post by charles.g.moore on 2006-09-18
I currently have 3 puters behind the same router (1 wireless connected desktop (wifes running XP) 1 ubuntu desktop (mine) and 1 ubuntu server box.
I only want the server box to be seen from the outside, i just want to host web page and see if I can connect to it.

I have given the server the ip 192.168.1.99 which is 1 below the range of IP's my router hands out (somebody said that will give me a static IP addy
but I still dont know what to put in my /etc/network/interfaces file

I can tell you that if i do an ipconfig on my wifes puter I get
netmask 255.255.255.0
network 192.168.1.0
b-cast  192.168.1.255
gateway 192.168.1.1

the ubuntu desktop addy is 192.168.1.101
my wifes XP is 192.168.1.102
and the server addy is 192.168.1.99

My router is set to assign 3 ip's starting at 192.168.1.100
and i have port forwarding set up (i think) on my router at port 443 pointing to 192.168.1.99

Sorry if this info is unneeded, im such a newb that I truthfully dont know exactly what info you need

---

### Post by chrisfay on 2006-09-18
> I have given the server the ip 192.168.1.99 which is 1 below the range of IP's my router hands out (somebody said that will give me a static IP addy
but I still dont know what to put in my /etc/network/interfaces file

This is correct. If you give your server a static IP address within the range handed down by your routers DHCP there will be conflicts; you are good giving your server any static ip under 192.168.1.100.

> I only want the server box to be seen from the outside, i just want to host web page and see if I can connect to it.

Not quite sure what you mean here. If you only want it seen from outisde your network, then giving your server an IP on your subnet will make the server available to all computers within your LAN. I assume you are ok with other pc's within your network viewing the server; if not, then you need to run your server on a different subnet. I will continue with the assumption you are ok with all your LAN pc's being allowed to communicate together.

Just for good measure, your servers /etc/network/interfaces file regarding the eth0 interface should look like this: (based on the IP 192.168.1.99 you mentioned)

auto eth0
iface eth0 inet static
address 192.168.1.99
netmask 255.255.255.0
gateway 192.168.1.1

If that's the case, and you can ping 192.168.1.99 from your other pc's, your LAN is communicating.

> i have port forwarding set up (i think) on my router at port 443 pointing to 192.168.1.99


Why did you forward port 443? This port is generally used for http protocol communication over TLS/SSL. If you are trying to host a website, you will want to forward port 80 to the ip 192.168.1.99. 

Once you do this, and you have apache successfully configured on your server, you will be able to browse to 24.253.31.187 in your internet broswer and should see apache's default page on your server. If not, you need to do some testing to see if your ISP blocks port 80, requiring some extra steps to circumvent this.

---


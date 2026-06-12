---
title: "Server as a router?"
date: 2011-01-13
forum: Server Platforms
---

### Post by Ranger_Joe on 2011-01-13
Hey Everyone,
I'm getting my first server in a few weeks. I hear a lot about people using their server as a router. That sounds like an interesting prospect, as I think it would increase security and control, with all web traffic going through one central hub so to speak.

If I do this, how do I handle wireless? Do I just hook my wireless router to my server, basically making the internet connection go through the server before it gets to the router?

Thanks for your help!

---

### Post by R.Bucky on 2011-01-13
I recommend leaving your server as a server and buying an embedded device such as a Soekris. Or, you can use a nettop computer. It is a huge space killer to use a dedicated box just for a router. If you want any scalability, such as wireless, you will need a switch anyways. Why not just go for the Soekris and do it the right way?

---

### Post by never say never on 2011-01-13
You can use a full blown computer as a router, but if you do, for security reasons,  it should not also be a server (Unless you want to set up virtual machines).

I much prefer using PFSense installed on an old system with multiple NICs because it offers me things that many routers don't.  Like Multiple VPN options, Multiple WAN interfaces with Load Balancing, fail over...  Even a Proxy server or many other options are available.  Then of course there is logging ...

The thing is you don't want to do firewalling on the same system you run other services on as there are security concerns.

---

### Post by perspectoff on 2011-01-13
A hardware router is only a few bucks these days. 

What you may be thinking of is creating a proxy server, which is a different animal. A proxy server is quite useful in a corporate or other large LAN. (It is overkill for a small home LAN and I wouldn't bother in that situation, though.)

In addition to DHCP, you can include DNS functions, filters, access restrictions, etc. on a proxy.

BTW, the term server is ambiguously used these days. A server is a software platform, although it is commonplace to refer to computers that host server software as servers.

It is important to note that any computer can host server software, and therefore even the most inexpensive computer can act as a server. Servers can also exist within virtual machines.

So "getting a server" doesn't really make that much sense. One can set up a server on almost any hardware.

---

### Post by sj1410 on 2011-01-13
> **Ranger_Joe said:**
> Hey Everyone,
I'm getting my first server in a few weeks. I hear a lot about people using their server as a router. That sounds like an interesting prospect, as I think it would increase security and control, with all web traffic going through one central hub so to speak.

If I do this, how do I handle wireless? Do I just hook my wireless router to my server, basically making the internet connection go through the server before it gets to the router?

Thanks for your help!

yes you can. it would be this way

internet-----eth1---server[firewall]==eth0===LAN_Switch===Wireless_Router

---

### Post by jbrown96 on 2011-01-14
Setup your hardware like sj1410 says. You can set this up in iptables with four commands, and you're done with the firewall.

```
ipables -P INPUT DROP
iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
iptables -t nat -A POSTROUTING -o eth1 -j ACCEPT
```

You can lock it down (or open it for services -- like SSH) more, but that will get it working with basic functionality.

You will also need to setup a DHCP server. 

I believe the Ubuntu package is dhcp-server. Install that with apt-get, and then edit your /etc/dhcp/dhcpd.conf for you LAN. 
You could go with something as simple as > authoritative;
subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.2 192.168.1.254;
option domain-name-server 192.168.1.1;
option routers 192.168.1.1;
}
```
service dhcp-server start
```
```
chkconfig dhcp-server on
```

Then assign yourself a static ip address of 192.168.1.1.

---

### Post by Ranger_Joe on 2011-01-14
Perspectoff, I was aware of that. I have heard of countless people turning their gaming consoles into "servers." Where it be a PS3 or 360... they make fine media servers.

---

### Post by Ranger_Joe on 2011-01-14
sj1410: What is the difference between eth1 and eth0?

jbrown96: That all seems very advanced. I will revisit this once I have my server.

---

### Post by R.Bucky on 2011-01-14
eth0 and eth1 are NIC assignments. Your first NIC would be labeled eth0 and the second would be eth1, etc... Just remember, that if you use a box for your router, make sure it is RAID and/or you have a quick backup in case of failure.

---


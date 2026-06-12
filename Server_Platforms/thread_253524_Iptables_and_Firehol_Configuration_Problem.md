---
title: "Iptables and Firehol Configuration Problem"
date: 2006-09-08
forum: Server Platforms
---

### Post by aek82 on 2006-09-08
I am currently running a server using Ubuntu Server 5.1 Breezy Badger. The purpose of this system is to serve as a gateway / firewall (iptables w/FireHol ) and content load balancer (Pound 1.9). 

The problem I am having is after configuring FireHol to open and forward port 80 traffic, a port scan using nmap reveals that port 80 is not open, or the status says closed. 

Please note that before I started FireHol (/etc/init.d/FireHol start), no ports were shown after running nmap. Nmap was run on a client outside of the private network.

My current firehol.config file looks like this:

```

version 5

interface eth0 internet
server http accept

interface eth1 private
server http accept
client all accept

router private2internet inface eth1 outface eth0
	route all accept

router internet2private inface eth0 outface eth1
	server http accept

```

no errors were generated after executing /etc/init.d/firehol start


Any suggestions or comments would be appreciated

The current network setup looks like

[SIZE="2"]Network Diagram[/SIZE]

[IMG]http://www.flyerdetails.com/network.jpg[/IMG]

---

### Post by JLTB on 2006-09-08
I don't have any experience with firehol, I use shorewall usually.  But when a port shows closed with nmap that means that it is getting through the firewall but your server (apache or whatever) isn't allowing traffic to connect to itself.

When nmap says your port is 'filtered' that's often a tricky situation to diagnose.  But in my experience open and closed indicate the data is passing the firewall at least.

---


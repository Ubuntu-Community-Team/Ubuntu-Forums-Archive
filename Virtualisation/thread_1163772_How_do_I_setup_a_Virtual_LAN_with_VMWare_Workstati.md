---
title: "How do I setup a Virtual LAN with VMWare Workstation?"
date: 2009-05-19
forum: Virtualisation
---

### Post by ivantheballer on 2009-05-19
**How do I setup a Virtual LAN with VMWare Workstation?**

:cry:
 
Im currently using VMware workstation n trying to create a mimic LANs across two countries from my laptops. The connections have to include IP address, subnet mask, domain name, default gateway and DNS server. In addition, how to show the connectivity from destop A's brower on network A to webserver on network B using a fake URL? 
 
Since I am just a poor beginner, anyone can give me a hand? Cos i just know how to unix on realii low level.....thanks heaps :)

---

### Post by superprash2003 on 2009-05-19
fake url meaning [http://myname](http://myname) or [http://x.x.x.x](http://x.x.x.x) where x.x.x.x is the ip?

---

### Post by ivantheballer on 2009-05-19
fake url meaning [[COLOR=#444444]http://myname[/COLOR]]("http://myname/") or [[COLOR=#444444]http://x.x.x.x[/COLOR]]("http://x.x.x.x/") where x.x.x.x is the ip?
__________________
 
it's non-numeric URL so it's not ip.
it should be sth like [http://www.myfakedomain](http://www.myfakedomain)..
 
thanks heaps 
 
i am now crying in front of my computer

---

### Post by superprash2003 on 2009-05-19
i guess you could do that by editing the /etc/hosts file.. just add whatever domainname you wish and its corresponding ip ( your local LAN ip)

---

### Post by ivantheballer on 2009-05-19
thx...

it means that i have to setup LANip before setting up DHCP? 

I am using dhcp3 pkt. 

Under /etc/dhcp3 

i've typed --> pico dhcpd.conf 

So i have to modify this conf file rite? How and what is the format of doing it? Thanks alot

---

### Post by superprash2003 on 2009-05-20
well you need to have a valid ip for networking ,so you should setup a static ip either using the network manager or by editing the /etc/network/interfaces file . then in the /etc/hosts file add something like this

192.168.1.2	myname.com

where 192.168.1.2 is the ip and myname.com is the domain you wish

---


---
title: "Closed ports problem"
date: 2010-03-25
forum: Server Platforms
---

### Post by tonypham on 2010-03-25
Hi all,

I have just built my home server from fresh, using Kubuntu 64 bit. I can access my server from both LAN and WAN for web (port 80) and ssh (port 22) services as well as ping it.

However, I can't access my server for ftp (port 21 - using proftpd) and Motion webcam server (port 8081) from both LAN and WAN.

A port forwarding web site told me that ports 21 and 8081 on my server are still closed but I don't know why because I have programs running and listening, the firewall seems not to block them:

nmap localhost:

21/tcp   open  ftp
22/tcp   open  ssh
25/tcp   open  smtp
80/tcp   open  http
143/tcp  open  imap
631/tcp  open  ipp
993/tcp  open  imaps
3306/tcp open  mysql
8080/tcp open  http-proxy
8081/tcp open  blackice-icecap

iptables -L -n:
...
Chain ufw-user-input (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:21
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:21
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:8081
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:8081
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:8080
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:8080
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:20
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:20

I can do ftp itself (ftp localhost) as well as access to webcam server locally (using [http://localhost:8081](http://localhost:8081)).

I have checked router's configure carefully (perhaps it is correctly set). BTW, I can't access from other LAN computers either (I have also changed my ADSL router from Dynalink to Billion but situation is the same).

I am stuck and don't know what to try nor what is the next step.

Can someones help me? Thanks a lot in advance.

---

### Post by KB1JWQ on 2010-03-26
It's a firewall issue.  Not sure which one, but it's a firewall issue. :-)

Can you nmap the box from itself targeting its private IP (NOT localhost) and get the same results?  If so, what does nmaping the box from another LAN machine return?

---

### Post by spynappels on 2010-03-26
You may need to specify that the rules apply to your ethernet connection as well as to the lo (Local Loopback) connection I had a problem recently where things were not working as expected, because I had opened a port on the eth0 interface but not on the lo interface in the firewall rules.

I also find the firewall easier to configure if I use the Webmin Interface.

---

### Post by KB1JWQ on 2010-03-26
Yeah, I hate webmin, but I'm also no wizard with iptables.  I'm torn. :-/

Just make sure that the rules aren't solely being applied to localhost; the lo interface is ONLY reachable from the machine itself.

---

### Post by tonypham on 2010-03-26
Oops, my big mistake.

After installing webmin, it shows me immediately that not only Linux firewall, but I have also other one: shorewall (installed when I was following a mail server installation tutor). I have removed it and now everything seems be under my control.

BTW, webmin is very impressive to me. I may "hate" it later but not now ;)

Thank you all very much. I highly appreciate.

---

### Post by spynappels on 2010-03-27
I have to admit that I sometimes love Webmin and sometimes hate it.

As long as you don't use it to try and configure Virtual Hosts in Apache or some other things, it works well. Hit a module where it does not work the Debian way and you're in big trouble. 

For Firewalls it is much better that Ebox IMHO, much more intuitive, and that is pretty much all I use Webmin for, oh and for Samba administration and some MySQL stuff.

---


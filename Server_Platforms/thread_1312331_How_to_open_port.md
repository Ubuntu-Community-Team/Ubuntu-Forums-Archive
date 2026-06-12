---
title: "How to open port"
date: 2009-11-03
forum: Server Platforms
---

### Post by srtata on 2009-11-03
Hi,

I am novice to Linux.  I have installed ubuntu9.10 on machine.  I want the team members to access a web application installed on this machine (using Jboss running at port 8080).  I have also apache running on this box.  Locally, I can access the web app, but others (who are in the same subnet 192.168.1.*) can not access this web app (say using [http://192.168.1.2:8080/webapp](http://192.168.1.2:8080/webapp)).

I have gone through the forum and few posts.  My understanding is firewall does not run.  

What should I do so that team members can access the web application from their machines (who are in the same subnet as my Linux box)?

Thanks 
Srinivas

=========== iptables -L -n gives ==============
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
===========================================

========= nmap -p8000-8999 localhost gives ========

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2009-11-03 12:44 IST
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on localhost (127.0.0.1):
Not shown: 996 closed ports
PORT     STATE SERVICE
8009/tcp open  ajp13
8080/tcp open  http-proxy
8083/tcp open  unknown
8093/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 0.16 seconds
=====================================================

=============== tcpdump gives the following when I access using 192.168.1.2/webapp ===================
tcpdump: listening on any, link-type LINUX_SLL (Linux cooked), capture size 96 bytes
12:41:37.734652 IP (tos 0x0, ttl 128, id 30576, offset 0, flags [DF], proto TCP (6), length 48)
    192.168.1.10.2177 > mercury-desktop.local.http-alt: Flags [S], cksum 0x4b4b (correct), seq 133989682, win 65535, options
[mss 1260,nop,nop,sackOK], length 0
12:41:37.734706 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 40)
    mercury-desktop.local.http-alt > 192.168.1.10.2177: Flags [R.], cksum 0x7733 (correct), seq 0, ack 133989683, win 0, leng
th 0
12:41:38.307390 IP (tos 0x0, ttl 128, id 30579, offset 0, flags [DF], proto TCP (6), length 48)
    192.168.1.10.2177 > mercury-desktop.local.http-alt: Flags [S], cksum 0x4b4b (correct), seq 133989682, win 65535, options
[mss 1260,nop,nop,sackOK], length 0
12:41:38.307421 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 40)
    mercury-desktop.local.http-alt > 192.168.1.10.2177: Flags [R.], cksum 0x7733 (correct), seq 0, ack 1, win 0, length 0
12:41:38.744893 IP (tos 0x0, ttl 128, id 30580, offset 0, flags [DF], proto TCP (6), length 48)
    192.168.1.10.2177 > mercury-desktop.local.http-alt: Flags [S], cksum 0x4b4b (correct), seq 133989682, win 65535, options
[mss 1260,nop,nop,sackOK], length 0
12:41:38.744926 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 40)
    mercury-desktop.local.http-alt > 192.168.1.10.2177: Flags [R.], cksum 0x7733 (correct), seq 0, ack 1, win 0, length 0
=============================================================

---

### Post by sliketymo on 2009-11-03
In a terminal,code(type in)" man ufw",without quotes.You will be able to see a great deal of information relating to forewall configuration.

---

### Post by TheTilde on 2009-11-03
I'm not a specialist at all. But here is my take:
- When you access locally the webapp, do you access with [http://127.0.0.1:8080/webapp](http://127.0.0.1:8080/webapp) or with [http://192.168.1.x:8080/webapp](http://192.168.1.x:8080/webapp) ? Both work?
- I don't know Jboss, but some web servers have the option to block access from remote hosts, only allowing local access. In case of apache, it may be in /etc/apache/config or something like this. Maybe Jboss has too a config file in /etc directory preventing remote access?

---


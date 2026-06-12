---
title: "snmp not allowing outside query"
date: 2010-05-16
forum: Server Platforms
---

### Post by xkaliburx on 2010-05-16
Odd behavior and not sure why.  I have 8 webservers all running u9.10, identical hardware, etc. I installed zenoss for monitoring, and installed snmp on each server.  Each server has the exact snmpd.conf file as reccomended by zenoss (nothing but rocommunity public), and restarted that daemon.

The 1st 2 servers connect and display fine but 3-8 dont.  There all on the same switch, network, and from zenoss I can ping 1-8, even ssh into 1-8, but an snmpwalk -v1 -cpublic server fails on 3-8.  I made sure iptables is not running, even stopped apparmor (trying everything).  I can even portscan the remote server using nmap but it just times out when using snmpwalk.

I don't remember booting the 1st 2 box's but dont see why that would help, but any other ideas/suggestions as to why it would fail on these is appreciated.

---


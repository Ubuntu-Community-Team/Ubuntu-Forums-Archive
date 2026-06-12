---
title: "telnet: Unable to connect to remote host: Connection refused"
date: 2010-06-21
forum: Virtualisation
---

### Post by winipcfg on 2010-06-21
Dear all,

I am a beginner of Ubuntu and VMWare. Recently, I have setup VMware in my local desktop and install Ubuntu server 8.04 as VM. I set the network mode as "NAT" mode and can ping the local desktop

To test the network of Ubuntu server, I tried to telnet to my intranet servers and it is confirmed to be okay. But I failed to telnet somewhere outside using my Ubuntu VM while I am able to do the same stuff in my local desktop. Here is the message shown in my Ubuntu VM

> 
$telnet [www.yahoo.com]("http://www.yahoo.com") 80
Trying xx.xxx.xxx.xx...
Trying xx.xxx.xxx.xx...
telnet: Unable to connect to remote host: Connection refused
The OS of My local desktop is windows XP. My desktop has enable firewall client and therefore there must be some ports blocked by the firewall. But as the network is NAT mode, I should be able to do the same stuff using same IP of my desktop. Is there something I have missed?

Thank you for any help. Thanks

---


---
title: "howe to close ping on ubuntu Server ??"
date: 2012-10-13
forum: Security
---

### Post by rzeer on 2012-10-13
Hi ,
 
Howe to close ping all time on ubuntu Server ??
 
and howe to make Fast connection to Ununtu Server , Contact fast and to UBUNTU Server

---

### Post by hydn79 on 2012-10-13
What do you mean close ping? What command are you using?

---

### Post by uRock on 2012-10-13
This link may be helpful, [http://askubuntu.com/questions/17548/how-can-i-block-ping-requests-with-iptables](http://askubuntu.com/questions/17548/how-can-i-block-ping-requests-with-iptables)

or

[http://unix.stackexchange.com/questions/14953/iptables-drop-all-incoming-icmp-requests-except-from-one-ip](http://unix.stackexchange.com/questions/14953/iptables-drop-all-incoming-icmp-requests-except-from-one-ip)

---

### Post by rzeer on 2012-10-13
> **hydn79 said:**
> What do you mean close ping? What command are you using?
 
I am using ubuntu Server 10.04
 
I want to close ping
 
-----------------
 
example - 
 
ping 213.14.231.196
 
i want to see - requset
 
and want to close the ping all time , can you help me ?

---

### Post by The Cog on 2012-10-13
My advice is to allow pings - they are useful for faultfinding.

However, if you want to block pings, you need to decide what to block. Do you want to prevent other users pinging your server, or do you want to block your server from pinging other machines? What about ICMP Unreachable messages - do you want to block them too? Either way, if you follow the links uRock gave, you should be able to work it out. If not, come back and explain exactly what you want to block.

As for "make Fast connection to Ununtu Server", I know the server likes to do a DNS lookup to find the name of whoever is connecting to it. If the DNS setup is wrong, this can take time to decide it doesn't know the name. It can help to put the name and IP address of clients into either the DNS server or into your server's /etc/hosts file to speed up this name resolution.

---

### Post by rzeer on 2012-10-13
> **The Cog said:**
> My advice is to allow pings - they are useful for faultfinding.
 
However, if you want to block pings, you need to decide what to block. Do you want to prevent other users pinging your server, or do you want to block your server from pinging other machines? What about ICMP Unreachable messages - do you want to block them too? Either way, if you follow the links uRock gave, you should be able to work it out. If not, come back and explain exactly what you want to block.
 
As for "make Fast connection to Ununtu Server", I know the server likes to do a DNS lookup to find the name of whoever is connecting to it. If the DNS setup is wrong, this can take time to decide it doesn't know the name. It can help to put the name and IP address of clients into either the DNS server or into your server's /etc/hosts file to speed up this name resolution.
 
 
when i enter this command
 
echo 0 > /proc/sys/net/ipv4/icmp_echo_ignore_all 
 
 
I am disable the ping on server , but when i restart the server , the ping it enable ?

---

### Post by The Cog on 2012-10-13
> **rzeer said:**
> when i enter this command
 
echo 0 > /proc/sys/net/ipv4/icmp_echo_ignore_all 
 
 
I am disable the ping on server , but when i restart the server , the ping it enable ?

Ah yes, that just changes the current setting. It won't survive a reboot. The file where you make those settings permanent is /etc/sysctl.conf. I guess you need a line adding like:
```
net.ipv4.icmp_echo_ignore_all = 0
```

---

### Post by cprofitt on 2012-10-14
don't forget about IPv6 if it is in your environment.

---


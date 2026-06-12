---
title: "Server Consolidation...what firewall would u recommend?"
date: 2011-01-15
forum: Security
---

### Post by mrchip on 2011-01-15
I am trying to consolidate my servers for a small office (less than 50 computers) and need file sharing/crm or erp database/backup/ftp/firewall/vpn etc). I was going to use endian but that seems to want to run on it's own machine.
 
I was going to run endian in Sun's virtualbox. While researching I have found both guarddog and Lutelwall should work within Ubuntu (no virtual machine needed).
 
1. Is there a reason to use Endian over Lutelwall or Guarddog?
2. Is there any reason NOT to run a firewall within a VM on the server?
3. Should I just scrap the whole idea and run a router flashed with dd-wrt or tomato
 
Thanks very much

---

### Post by HermanAB on 2011-01-16
Howdy,

If your servers are configured right, then you do not need a firewall.  Services that you do not want listening, should be shut down, not blocked in a firewall.

I just use a one line iptables rate limit rule to protect against all kinds of DOS attacks.

---

### Post by mrchip on 2011-01-16
Thanks for the reply.  What about a VPN or IDS?  
 
I think one of the requirments to meet govt reg's I must abide in for clients that are backing up to my server is a firewall.

---

### Post by mrchip on 2011-01-16
Thanks for the reply.  What about a VPN or IDS?  
 
I think one of the requirments to meet govt reg's I must abide in for clients that are backing up to my server is a firewall.

---

### Post by wacky_sung on 2011-01-16
> **HermanAB said:**
> Howdy,

If your servers are configured right, then you do not need a firewall.  Services that you do not want listening, should be shut down, not blocked in a firewall.

I just use a one line iptables rate limit rule to protect against all kinds of DOS attacks.

Probably you show me your one line of iptables which block all kinda DDOS attacks.I am very doubtful about it.

---

### Post by spynappels on 2011-01-17
To the OP, you might be fine running a router with a version of dd-wrt which includes a OpenVPN server, it will also have IPTables on it as it is a Linux based firmware, and you can write any rules you want for it.

---

### Post by spynappels on 2011-01-17
Multiple post

---

### Post by spynappels on 2011-01-17
Multiple post

---

### Post by HermanAB on 2011-01-17
```
# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT

```

---

### Post by wacky_sung on 2011-01-18
> **HermanAB said:**
> ```
# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT

```

FYI this cannot stop people making smurf attack or spoof attack on you.Inregard of how good your configuration until this day nobody can stop a botnet to down your server/network by mean of ddos.What you really need is enough bandwidth to combat with ddos even with all good configuration.

---


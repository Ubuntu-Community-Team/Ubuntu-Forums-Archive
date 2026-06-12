---
title: "Squid flooded with TIME_WAIT need a fix urgent!"
date: 2011-08-08
forum: Server Platforms
---

### Post by binbashnz on 2011-08-08
Hi,

We have implemented a Ubuntu with Squid (2.7) & Dansguardian,
 Webmin, and the webmin modules for these services.

Server was running fine for about 6 months then suddenly
there are hundreds of TIME_WAIT's when using 
```
netstat -antup
```
This causes the clients to get this error on their browser:
```
commBind: Cannot bind socket FD 10 to *:0 (98) Address already in use
```

Even 1 single client working will fill 3 pages of TIME_WAIT

Clients are Mac's bound to OD & AD (magic triangle).

We reverted the vm image to a snapshot back when was working fine but problem remains. 
We created a server from scratch and same issue.

We use **ldap_auth** to the active directory for authentication
Server is 2008 R2

Any ideas how to fix this?

I can provide more info if requested.

Thanks alot.

---

### Post by Vishal Agarwal on 2011-08-08
Is some problem with firewall ?

---

### Post by rubylaser on 2011-08-08
This sounds like a networking problem more than a problem with the actual host (since you've restored from a previous know backup).  What's does the output of ifconfig look like?  And have you tried to disable networking on the Squid Proxy and verified that no other devices on the network are trying to use the same ip address? Or, is something else trying to use Squid's port.  What does this show?
```
netstat -na inet | grep LISTEN
netstat -na | grep 8080
```

Or, you have run out of free ports, and all available ports occupied by TIME_WAIT sockets. 
Things to look into 
1. I'd stop squid, and leave it off for a minute (kill it if it's stuck).
2. Configure the unassigned port range from 1024-65535. In 
Ubuntu this is set in /proc/sys/net/ipv4/ip_local_port_range. This should allow around 500 connections.

---

### Post by binbashnz on 2011-08-09
> **Vishal Agarwal said:**
> Is some problem with firewall ?

Nothing was changed on the firewall, why would this happen after 6 months?

---

### Post by binbashnz on 2011-08-09
> **rubylaser said:**
> This sounds like a networking problem more than a problem with the actual host (since you've restored from a previous know backup).  What's does the output of ifconfig look like?  And have you tried to disable networking on the Squid Proxy and verified that no other devices on the network are trying to use the same ip address? Or, is something else trying to use Squid's port.  What does this show?
```
netstat -na inet | grep LISTEN
netstat -na | grep 8080
```

Or, you have run out of free ports, and all available ports occupied by TIME_WAIT sockets. 
Things to look into 
1. I'd stop squid, and leave it off for a minute (kill it if it's stuck).
2. Configure the unassigned port range from 1024-65535. In 
Ubuntu this is set in /proc/sys/net/ipv4/ip_local_port_range. This should allow around 500 connections.


All the Time_Wait happens on ports 3128, 8080

We already increased port_range.

We tried with persistent on /off nothing improved.

We stopped squid, restarted, restarted proxy, reverted to original snapshot. Installed new linux from scratch. Still same issue.

It's worth to point out that the issue happens on Mac clients only, Windows client are fine.


I get this:

TCP 10.99.1.253:8080 172.16.0.30:<random port> TIME_WAIT

repeated for about 10-15 pages just from 1 computer (1 ip). When more computers connected there are thousands of entries.

---


---
title: "Cannot ping Ubuntu machine from other machines on network"
date: 2018-04-16
forum: Security
---

### Post by shadix37 on 2018-04-16
Hey guys,
So I'm having issues with my Ubuntu 16.04 machine. I am able to ping devices on the network from the Ubuntu machine and hit all of them, but am unable to ping Ubuntu from any other device on the network. I have the firewall down on Ubuntu and my Windows 8 machine. Any ideas what I may be missing? Also note that I am by no means savvy with Ubuntu, so forgive my ignorance. 
Thanks!

---

### Post by TheFu on 2018-04-17
Welcome to the forums.

Ping by IP or ping by name?
IP should always work if the network config is correct and the IP is correct on both machines involved.

So ... to troubleshoot, 
ifconfig
route -n
ping {IP address}

pinging by name isn't as easy.  IP networking doesn't announce names, so either the /etc/hosts or DNS needs to be configured.  If you haven't done either, using names won't work.

---

### Post by delfiler on 2018-04-18
TheFu is right about what he says

i walked in to this problem (well a solution for me) before.
but do you have this line of code in a script or file or in /sbin/iptables?
```

$IPTABLES -A (chain name) -p icmp --icmp-type (mask or comp name (not as in company)) -j (target name)

```
there might/will be multiple of this line of code cause this line can prevent or allow you to pinging to or from your machine

---


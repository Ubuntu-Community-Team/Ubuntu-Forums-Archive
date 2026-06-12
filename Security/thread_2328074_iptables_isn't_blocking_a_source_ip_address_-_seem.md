---
title: "iptables isn't blocking a source ip address - seems disabled or otherwise ineffective"
date: 2016-06-17
forum: Security
---

### Post by andrew305 on 2016-06-17
**Objective**: I would like to be able to block an IP address from having any/all connections to my server running Ubuntu 16.04 and strictly iptables.

**Background**: I've read tutorials and troubleshooting articles, so I know how the implementation should work, but it's not. I'm starting fresh to troubleshoot, so I have flushed my entire iptables, uninstalled and purged ufw, erased all but the standard INPUT/OUTPUT/FORWARD chains, and am currently trying to block one of my other devices so I'm able to test realtime.

**Problem/Observation**: Despite my iptables seemingly being configured correctly, I am still able to connect to the server through the device with the IP in rule #1 on both SSH and other specific service ports.

**_sudo iptables -L -n -v --line-number_** (IP address redacted for security):

```
Chain INPUT (policy ACCEPT 205K packets, 27M bytes)
num   pkts bytes target     prot opt in     out     source               destination         
1        0     0 DROP       all  --  *      *       107.##.###.###       0.0.0.0/0           
2     3757  318K ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22


Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
num   pkts bytes target     prot opt in     out     source               destination         


Chain OUTPUT (policy ACCEPT 287K packets, 177M bytes)
num   pkts bytes target     prot opt in     out     source               destination     
```

**Comments**: The behavior seems similar to a firewall that is turned off, as I would occasionally do with ufw while testing previous solutions.  From what I understand, in Ubuntu 16.04, rules inside iptables are 'active,' and don't require/allow the STOP/START/ENABLE/DISABLE/RESTART/STATUS service functions like ufw does.  I'm trying strictly with iptables now instead of ufw/gufw because while trying to legitimately block IP address previously, I was detecting their connections coming back even after service restarts and reboots.

Any suggestions or recommendations?

---

### Post by andrew305 on 2016-06-17
For some reason, my alternate device gives one IP when doing a standard 'my ip' query, but the SSH is logging a different IP, so that's why it wasn't blocking effectively.

---


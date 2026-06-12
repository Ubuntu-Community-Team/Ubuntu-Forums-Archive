---
title: "sysctl not sticking after reboot"
date: 2019-02-18
forum: Security
---

### Post by tsutsudidz on 2019-02-18
Using ```
Lubuntu 18.10 Cosmic Cuttlefish
```

Most commands do stick. However Lynis has repeatedly demonstrated four sysctl 
parameters are not sticking on reboot. 

```
    fs.suid_dumpable (exp: 0)
    net.ipv4.conf.all.log_martians (exp: 1) 
    net.ipv4.conf.all.rp_filter (exp: 1)     
    net.ipv4.conf.default.log_martians (exp: 1)  
```

 
The one I am most concerned about is ```
net.ipv4.conf.all.rp_filter
``` which should be set to 1, but is set to 0... leaving the machine vulnerable to ip spoofing. How can I ensure these are set properly upon boot?

sysctl -p does successfully apply them after the system has started. If you are going going to say, write a script, please provide details on how it is done. Thank you!!

---

### Post by tsutsudidz on 2019-02-18
**1. net.ipv4.all.rp_filter=1 rectified.** After some testing I disabled wireguard VPN  on boot and this rectified all.rp_filter; via ubuntu's website:  "net.ipv4.conf.all.rp_filter = 1. Checks our routing table against the  source address of incoming packets to make sure that they're coming from  the interface our routing table says that address is on. Note that this  needs to be easily disabled; if some form of advanced routing or policy  routing intends traffic from a host to come in one interface and  traffic to that host to leave out a different interface, then legitimate  packets will be dropped."

[source]("https://wiki.ubuntu.com/ImprovedNetworking/KernelSecuritySettings")

In my case I can safely leave this disabled.[B]

2. net.ipv4.conf.*.log_martians Rectified[/B]
    
net.ipv4.conf.all.log_martians=1
    net.ipv4.conf.default.log_martians=1

by searching for all sysctl.conf on the system via command: **find / -name '*sysctl*.conf'** I found ufw firewall  **/etc/ufw/sysctl.conf** overruled **/etc/sysctl.conf** log_martians, resulting in them being disabled. Changing them rectified this issue.

**3. fs.suid_dumpable=0**

I still cant figure out how to disable "fs.suid_dumpable" on boot.

---


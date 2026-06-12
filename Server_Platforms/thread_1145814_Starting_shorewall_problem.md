---
title: "Starting shorewall problem"
date: 2009-05-02
forum: Server Platforms
---

### Post by satimis on 2009-05-02
Hi folks,

Ubuntu 8.04
Shorewall

Shorewall fails to start;

# /etc/init.d/shorewall start```

Starting "Shorewall firewall": not done (check /var/log/shorewall-init.log).

```


# tail /var/log/shorewall-init.log```
 
Perhaps ip6tables or your kernel needs to be upgraded.
ip6tables v1.3.8: can't initialize ip6tables table `filter': iptables who? (do you need to insmod?)
Perhaps ip6tables or your kernel needs to be upgraded.
ip6tables v1.3.8: can't initialize ip6tables table `filter': iptables who? (do you need to insmod?)
Perhaps ip6tables or your kernel needs to be upgraded.
ip6tables v1.3.8: can't initialize ip6tables table `filter': iptables who? (do you need to insmod?)
Perhaps ip6tables or your kernel needs to be upgraded.
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
Terminated

```

/# uname -r```

2.6.24-23-openvz

```

OpenVZ kernel is running here.  Please advise how to fix the problem.  TIA


B.R.
satimis

---


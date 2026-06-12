---
title: "UFW firewall and network device"
date: 2018-02-10
forum: Security
---

### Post by jsvidyad on 2018-02-10
Hello,

    I have a question. I run ubuntu 16.04. I have UFW firewall enabled with incoming set to DENY and outgoing set to ALLOW. In the UFW firewall, there is no network device mentioned. So, my question is, will the firewall be active and protect my system irrespective of which network device I am using to access the internet??

---

### Post by TheFu on 2018-02-10
yes.

UFW isn't the firewall, it is an interface to the system firewall which is part of the kernel.

You can see the rules using other firewall interface programs, like iptables.  ```
sudo /sbin/iptables -L
``` Firewall rules **may** be per interface, but they usually aren't on Linux systems.

---


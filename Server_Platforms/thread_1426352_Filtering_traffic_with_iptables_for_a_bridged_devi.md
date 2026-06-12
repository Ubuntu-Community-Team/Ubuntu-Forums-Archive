---
title: "Filtering traffic with iptables for a bridged device?"
date: 2010-03-10
forum: Server Platforms
---

### Post by tauren on 2010-03-10
I can't seem to figure out how to filter traffic when using a bridge. I've got an Ubuntu 9.10 server with KVM installed and have configured br0. I have several VMs online with web servers running and everything is working. Note that all VMs have dedicated IP numbers, I am not using DHCP or NAT.

I want to add a firewall only on the HOST system, not in the VMs, and I want to be able to control what ports are open to the hosts as well as redirecting certain ports (i.e. 80 -> 8080). I do not want to run iptables on the VMs, only on the HOST.

I've added the following to /etc/sysctl.conf:

```
net.bridge.bridge-nf-call-arptables = 1
net.bridge.bridge-nf-call-iptables = 1
net.bridge.bridge-nf-call-ip6tables = 1
net.bridge.bridge-nf-filter-vlan-tagged = 1

```

Then I ran:

```
sysctl -p /etc/sysctl.conf

```

I added a simple rule, thinking that the web servers running on port 8080 in the VMs would no longer be accessible:

```
iptables -I FORWARD -j DROP -p tcp -s 0/0 -d 0/0 --dport 8080

```

I also tried restarting the network. But I can still browse all the sites on port 8080 on all the VMs.  I've tried specifying specific IP numbers for the destination as well.

What am I doing wrong? 

Thanks,
Tauren

---


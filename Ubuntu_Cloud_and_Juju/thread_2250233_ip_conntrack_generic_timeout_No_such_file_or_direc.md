---
title: "ip_conntrack_generic_timeout: No such file or directory"
date: 2014-10-27
forum: Ubuntu Cloud and Juju
---

### Post by luckyknight on 2014-10-27
Hi,

I've followed a few guides on the internet to increase the limits for tcp/ip filtering such as those below:

/etc/sysctl.conf
net.netfilter.nf_conntrack_max=131072
net.ipv4.netfilter.ip_conntrack_generic_timeout=120
net.ipv4.netfilter.ip_conntrack_tcp_timeout_established=54000

These settings no long seem to be applying? Have they changed in newer kernels?

sysctl: cannot stat /proc/sys/net/ipv4/netfilter/ip_conntrack_generic_timeout: No such file or directory
sysctl: cannot stat /proc/sys/net/ipv4/netfilter/ip_conntrack_tcp_timeout_established: No such file or directory

Thanks

---

### Post by Doug S on 2014-10-28
The issue is that the files are not present until after the conntrack  module is loaded, which is typically sometime after the sysctl stuff runs. In my case the conntrack module is loaded when my iptables rule set loads, so I make the changes at the end of my iptables script. See [also]("http://ubuntuforums.org/showthread.php?t=2244444").

---


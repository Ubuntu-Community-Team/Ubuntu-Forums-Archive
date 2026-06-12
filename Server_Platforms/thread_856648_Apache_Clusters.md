---
title: "Apache Clusters"
date: 2008-07-11
forum: Server Platforms
---

### Post by DualFusion on 2008-07-11
Hi,

I have 5 servers:
1) Loadbalancer/Root
2) Apache node
3) Apache node
4) NFS
5) Mail

And I have been trying to get server1 to transfer data to each Apache node depending on there file type, not just what folder they are in. For example I may want to have PHP go to Apache node1 and Ruby into Apache node2

I have looked at the two tutorials with no success:
[http://www.howtoforge.com/set-up-a-loadbalanced-ha-apache-cluster-ubuntu8.04](http://www.howtoforge.com/set-up-a-loadbalanced-ha-apache-cluster-ubuntu8.04)
[http://www.howtoforge.com/reduce-apache-load-with-lighttpd-debian-etch](http://www.howtoforge.com/reduce-apache-load-with-lighttpd-debian-etch)

Thanks,
Kevin.

---

### Post by DualFusion on 2008-07-11
Forgot to note that I also want server1 to be DNS. So I basically want a solution that would let me install DNS and would also load-balance between my 2 apache nodes, but will make sure all PHP files go to node1 while all Ruby goes to node2.

Thanks,
Kevin.

---

### Post by DualFusion on 2008-07-12
*bump*

---

### Post by DualFusion on 2008-07-12
Can't someone help? Please? This is really important and can't continue without this step. I have been stuck with this problem for a couple days now. Any help is much appreciated.

Thanks,
Kevin.

---


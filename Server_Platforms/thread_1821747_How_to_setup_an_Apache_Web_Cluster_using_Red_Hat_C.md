---
title: "How to setup an Apache Web Cluster using Red Hat Cluster Suite"
date: 2011-08-09
forum: Server Platforms
---

### Post by aldav on 2011-08-09
Hello, I am working in a project that needs to set up an Apache Web Cluster. The cluster needs to be High-availability (HA) cluster and Load-balancing cluster. Someone mentioned the use of Red Hat Cluster Suite, but, honestly, I can't figure out how it works, I haven't been able to configure it correctly. The project currently have two nodes, but we need to support at least three nodes in the cluster.
Can anyone help me through this? Or point me to a tutorial I can read?

Thanks in advance

---

### Post by Evilware on 2011-08-12
Docs found at [https://access.redhat.com/knowledge/docs/](https://access.redhat.com/knowledge/docs/)

---

### Post by aldav on 2011-08-12
This is the message I get when I try to access resources from Red Hat site:

"........The resource you requested is available exclusively to Red Hat customers with an active Red Hat or JBoss subscription......."
"........If you don't have an active subscription, we encourage you to consider purchasing one..........."

I can't buy an active subscription, so the site can't help me. Maybe if someone can tell me where to get access to the same documentation for free?

---

### Post by ingeva on 2011-08-13
> **aldav said:**
> This is the message I get when I try to access resources from Red Hat site:
....
I can't buy an active subscription, so the site can't help me. Maybe if someone can tell me where to get access to the same documentation for free?
I really don't know if it would help in this situation, but maybe you should consider cloud computing?  Don't ask me how to do it though .... :)

---

### Post by SeijiSensei on 2011-08-14
Try CentOS.  It's a free respin of RedHat Enterprise Linux.  I also found some documentation for clustering taken straight from RH like this: [http://www.centos.org/docs/5/html/5.1/Cluster_Administration/](http://www.centos.org/docs/5/html/5.1/Cluster_Administration/)

---

### Post by aldav on 2011-08-15
I managed to create an Apache Web Cluster without using Red Hat Cluster Suite. I used HAProxy and Heartbeat. I followed a great tutorial in this url: [http://www.ctrip.ufl.edu/apache2-cluster-in-debian-lenny-howto]("http://www.ctrip.ufl.edu/apache2-cluster-in-debian-lenny-howto")
However, I'm still missing one piece. I managed to create a HA-LB Apache cluster, but www home folder at this moment may differ from one cluster to another. This is undesirable, because I need to maintain the same files across the cluster nodes. How can I achieve this? I have used DRBD with OCFS2, but DRBD support only two nodes (three at most), but I need multiple nodes (more than three). I need to maintain the www home folder synchronized in real time (by this, I mean I don't want to use rsync). Is this achievable? Any hints?


Thanks in advance

I forgot to mention. Everything needs to be set up in Debian.

---


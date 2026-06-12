---
title: "How do you plan fail over redundancy design for shared/VPS hosting ?"
date: 2016-08-16
forum: Ubuntu, Linux and OS Chat
---

### Post by soamz on 2016-08-16
We are looking to offer shared hosting and VPS hosting both to our 1000+ clients who are ready to subscribe to us. 
I know, no hosting company takes auto backup of each second for shared hosting clients or VPS clients without extra charge, but Im looking to do that for my clients. 

so, how should I design it ?

I need a completely 100% disaster proof design, so that even if a server gets burnt or goes dead for any reason, we should be able to get the clients up and running with where they left immediately. 
Im sure, there are ways to do this, just dont know what needs to be done. 


Our architecture is, 
we have dedicated super micro for shared clients. 
we have dedicated super micro for VPS hosting. 

Do we need one more server to act like a instant backup or clone image of the above 2 servers ?

So, that if someday the above servers die, then we can simply fire up the 3rd backup server simply by changing its IP address or something like that ?

---

### Post by howefield on 2016-08-16
Zero to do with Ubuntu.

Moved to a non support forum.. "Ubuntu, Linux and OS Chat"

---

### Post by grahammechanical on 2016-08-16
[https://jujucharms.com/about](https://jujucharms.com/about)

[http://insights.ubuntu.com/2016/08/15/lunch-learn-with-openstack-containers/](http://insights.ubuntu.com/2016/08/15/lunch-learn-with-openstack-containers/)

Regards

---

### Post by Old_Grey_Wolf on 2016-08-16
You may want to look into the OpenStack High Availability guide. [http://docs.openstack.org/ha-guide/](http://docs.openstack.org/ha-guide/)

Here is a comparison of OpenStack and VMware high availability and fault tolerance models. [https://www.mirantis.com/blog/cloud-prizefight-vmware-vs-openstack/](https://www.mirantis.com/blog/cloud-prizefight-vmware-vs-openstack/) It is old but still relevant.

---


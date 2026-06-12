---
title: "Cross Environment Relations"
date: 2015-11-03
forum: Ubuntu Cloud and Juju
---

### Post by eallain-poctu on 2015-11-03
The following link leads to one section of the roadmap in 2014 [https://github.com/juju/juju/blob/dafe43b5683c9b22af86ee744a8ea7f088b087b6/doc/contributions/juju-14-10-plans.md#cross-environment-relations](https://github.com/juju/juju/blob/dafe43b5683c9b22af86ee744a8ea7f088b087b6/doc/contributions/juju-14-10-plans.md#cross-environment-relations)
I would like to know if there is any news on this subject.

I'm basically installing Cassandra and I would like to create one multi datacenter cluster (that means at least 2 environments). 
EC2MultiRegionSnitch requires that some units of each environment need to know some public ips of the other environment to let Cassandra discover all nodes.

Is there any workaround to achieve cross environment relation ?

Following the link, several lines below, there's a note which describes a mechanism of endpoint exposition but I don't get how to configure it. 

If someone has an example or an idea, let me know.
Thanks !

---


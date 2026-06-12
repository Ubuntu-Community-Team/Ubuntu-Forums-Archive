---
title: "high availability and clustering"
date: 2009-06-01
forum: Server Platforms
---

### Post by salim.madni on 2009-06-01
dear gurus

advise suggest and comments what are all possible clustering, high availbility solution available under ubuntu server enviornment.

also can some one point out what are opensource and what are paid/commercial

i found heartbeat(DRBD) and linux-ha

but i have confusion to understand clearly. the first question is it compatible with our ubuntu 8.04 LTS or later on or not. is it certify safe to use

can some one share his own experience testing or production results

we need to make parallel cluster of email server base on ubuntu. which is part of disaster recovery plan. if 1st server get crashed or burn(office premises) so other server come one automaticaly

regards
salim

---

### Post by akakijevic on 2009-08-05
is there any progress on this theme??
any link would be great

I'm dealing with same issue

---

### Post by koenn on 2009-08-06
it exists : [http://www.linux-ha.org/](http://www.linux-ha.org/)

but integration in Ubuntu Server is still only in the "let's see how we could do this ' phase

[https://blueprints.edge.launchpad.net/ubuntu/+spec/server-karmic-cluster-stack](https://blueprints.edge.launchpad.net/ubuntu/+spec/server-karmic-cluster-stack)
[https://wiki.ubuntu.com/ClusterStack](https://wiki.ubuntu.com/ClusterStack)

---

### Post by inertz on 2009-10-22
I'm also interested with this issue. Perhaps someone expert in this field can briefly explain about it.

---


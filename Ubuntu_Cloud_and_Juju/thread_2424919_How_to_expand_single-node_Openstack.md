---
title: "How to expand single-node Openstack"
date: 2019-08-17
forum: Ubuntu Cloud and Juju
---

### Post by kjetil-fleten on 2019-08-17
Hi,

Is it possible to expand a single-node OpenStack built with conjure-up with with an extra node later ?

---

### Post by digikin on 2020-01-19
If you installed the snap I don't see it being possible to expand. [https://opendev.org/x/microstack/src/branch/master/snap-overlay/snap-openstack.yaml](https://opendev.org/x/microstack/src/branch/master/snap-overlay/snap-openstack.yaml)
But if you installed it using juju your can just scale if needed.

---


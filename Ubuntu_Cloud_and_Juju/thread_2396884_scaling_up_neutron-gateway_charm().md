---
title: "scaling up neutron-gateway charm(?)"
date: 2018-07-22
forum: Ubuntu Cloud and Juju
---

### Post by ekalaya2015 on 2018-07-22
Hi all,
I am sorry if this question sound silly, but I am so curious.
I already deployed openstack queen using juju on to 10 machines. I used openstack base bundle as initial configuration and modified it for HA purpose
Machine configuration as follow:
3 machines as storage (ceph backed)
3 machines as compute
3 machines as controller and configured as HA clustered
1 machine as network node. Neutron-API and Neutron-gateway deployed into it.
If I want to configure this network node as HA clustered, Should I scale up neutron-gateway app or no? There is no text in it's reference about scaling-up. One more thing there is no vip config in this charm.
Thank you

---

### Post by matthiashuether on 2018-12-13
Any news here? I have the same question. Here is a info: [https://jujucharms.com/openstack-base/](https://jujucharms.com/openstack-base/)

[I]Neutron Gateway, Nova Compute and Ceph services are designed to be horizontally scalable.

[/I]*To horizontally scale Neutron Gateway:*

 juju add-unit neutron-gateway # Add one more unit
juju add-unit -n2 neutron-gateway # Add 2 more unitsa
Maybe this is all to do for scaling neutron-gateway charm as ha-cluster... but I do not know if there is anything else to consider.

---

### Post by ekalaya2015 on 2018-12-13
thank you for your response. you are right that is all to do to scale neutron-gateway horizontally and seems nothing else. I already did those thing and tested by shutting down one of neutron-gateway and seems cluster still works well.

---

### Post by matthiashuether on 2018-12-16
sounds good...   did you use the ha-cluster charm [https://jujucharms.com/hacluster/](https://jujucharms.com/hacluster/) ? Or only a new neutron-gateway charm?
Have you configured other things in the neutron-gateway charm like interfaces or ip?

---

### Post by ekalaya2015 on 2018-12-20
I used only neutron-gateway charm, that's all, nothing fancy to be setup:D

---

### Post by ekalaya2015 on 2018-12-20
oh forgot one thing, I deployed neutron-gateway charm directly on to root machine and config as follow:
juju config neutron-gateway bridge-mappings='physnet1:br-ex'
juju config neutron-gateway data-port=br-ex:eno2
juju config neutron-gateway ha-bindiface=eno1

of course interface name have to follow yours

---

### Post by matthiashuether on 2019-05-14
Thank you that worked!

---


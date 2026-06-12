---
title: "How to solve ubuntu openstack instance error “no valid host found”?"
date: 2014-10-13
forum: Ubuntu Cloud and Juju
---

### Post by vish garg on 2014-10-13
I've deployed openstack using juju and tried to launch a new instance  which gives an error "no valid host was found". I've checked out other  questions on this community and across the web with same problem and  tried all but, nothing seems to work for me. I've also tried to create a  volume from an image and then launch an instance but, nothing works.
  nova-manage service list is showing all is correct.
  here is the nova-compute log: [http://pastebin.com/et47GiHt](http://pastebin.com/et47GiHt)
  I've three compute nodes, one with 4g ram 8 cpus and 400gb hdd,  second 16g ram 16cpus 1.1t hdd and third 4cpus 5g ram and 110g hdd.
  Output of nova-manage service list:


```
Binary           Host                                 Zone             Status     State Updated_At
nova-cert        nodethreehcl                         internal         enabled    :-)   2014-10-10 10:21:08
nova-scheduler   nodethreehcl                         internal         enabled    :-)   2014-10-10 10:21:17
nova-conductor   nodethreehcl                         internal         enabled    :-)   2014-10-10 10:21:10
nova-compute     nodefivedell                         nova             enabled    :-)   2014-10-10 10:21:09
nova-network     nodefivedell                         internal         enabled    :-)   2014-10-10 10:21:14
nova-compute     nodeoneibm                           nova             enabled    :-)   2014-10-10 10:21:10
nova-network     nodeoneibm                           internal         enabled    :-)   2014-10-10 10:21:14
nova-compute     nodefourdell                         nova             enabled    :-)   2014-10-10 10:21:13
nova-network     nodefourdell                         internal         enabled    :-)   2014-10-10 10:21:11
```


here is some nova-scheduler log:

> 2014-10-09 09:09:20.887 5395 INFO oslo.messaging._drivers.impl_rabbit [-] Reconnecting to AMQP server on localhost:5672 2014-10-09 09:09:20.887 5395 INFO oslo.messaging._drivers.impl_rabbit [-] Delaying reconnect for 1.0 seconds... 2014-10-09 09:09:21.898 5395 ERROR oslo.messaging._drivers.impl_rabbit [-] AMQP server on localhost:5672 is unreachable: [Errno 111] ECONNREFUSED. Trying again in 25 se conds. 2014-10-09 09:09:46.905 5395 INFO oslo.messaging._drivers.impl_rabbit [-] Reconnecting to AMQP server on localhost:5672 2014-10-09 09:09:46.905 5395 INFO oslo.messaging._drivers.impl_rabbit [-] Delaying reconnect for 1.0 seconds... 2014-10-09 09:09:47.915 5395 ERROR oslo.messaging._drivers.impl_rabbit [-] AMQP server on localhost:5672 is unreachable: [Errno 111] ECONNREFUSED. Trying again in 27 se conds. 2014-10-09 11:04:33.915 19829 WARNING nova.scheduler.driver [req-72151d54-0d5d-4478-8d89-47154defd5c0 3306d471e67c4735a2816fdc94ac9552 5dc1db60d64f46249e68a3498f914a18]  [instance: 39e0494c-6c75-46a0-b8b0-e45f9d52cd37] Setting instance to ERROR state. 2014-10-09 11:04:34.011 19829 INFO oslo.messaging._drivers.impl_rabbit [-] Connected to AMQP server on
192.168.2.166:5672 2014-10-09 11:13:14.985 19829 INFO nova.scheduler.filter_scheduler [req-531418dc-fde2-440c-8fb5-7e7d57b108a3 3306d471e67c4735a2816fdc94ac9552 5dc1db60d64f46249e68a3498f 914a18] Attempting to build 1 instance(s) uuids: [u'57d92c9f-9cee-42cc-ab08-94749e790401'] 2014-10-09 11:13:15.011 19829 INFO nova.filters [req-531418dc-fde2-440c-8fb5-7e7d57b108a3 3306d471e67c4735a2816fdc94ac9552 5dc1db60d64f46249e68a3498f914a18] Filter Imag ePropertiesFilter returned 0 hosts 2014-10-10 08:52:17.811 5076 WARNING nova.scheduler.driver [req-d07d057a-7ce6-4154-96b8-7640a16d4ec9 3306d471e67c4735a2816fdc94ac9552 5dc1db60d64f46249e68a3498f914a18] [instance: fa245933-d55b-4f68-90ce-ee7ab1deb536] Setting instance to ERROR state. 2014-10-10 09:03:58.055 5076 INFO nova.openstack.common.service [-] Caught SIGTERM, exiting 2014-10-10 09:03:58.783 14967 INFO nova.openstack.common.periodic_task [-] Skipping periodic task
_periodic_update_dns because its interval is negative 2014-10-10 09:03:58.830 14967 AUDIT nova.service [-] Starting scheduler node (version
2014.1.2) 2014-10-10 09:03:59.382 14967 INFO oslo.messaging._drivers.impl_rabbit [-] Connected to AMQP server on
192.168.2.166:5672 2014-10-10 09:04:17.220 14967 INFO nova.scheduler.filter_scheduler [req-f7e08c23-7689-4a1e-8184-99761e681c1b 3306d471e67c4735a2816fdc94ac9552 5dc1db60d64f46249e68a3498f 914a18] Attempting to build 1 instance(s) uuids: [u'e902fea6-9f30-450d-985d-9aca6f1e4e10'] 2014-10-10 09:04:17.254 14967 INFO nova.filters [req-f7e08c23-7689-4a1e-8184-99761e681c1b 3306d471e67c4735a2816fdc94ac9552 5dc1db60d64f46249e68a3498f914a18] Filter Imag ePropertiesFilter returned 0 hosts 2014-10-10 09:04:17.255 14967 WARNING nova.scheduler.driver [req-f7e08c23-7689-4a1e-8184-99761e681c1b 3306d471e67c4735a2816fdc94ac9552 5dc1db60d64f46249e68a3498f914a18]  [instance: e902fea6-9f30-450d-985d-9aca6f1e4e10] Setting instance to ERROR state. 2014-10-10 09:04:17.355 14967 INFO oslo.messaging._drivers.impl_rabbit [-] Connected to AMQP server on
192.168.2.166:5672

---

### Post by chris240 on 2014-10-23
Try adding in nova cloud controller nova.conf "scheduler_default_filters=AllHostsFilter"
Or if you using juju-gui in nova cloud controller in config flag string "scheduler_default_filters=AllHostsFilter"

---

### Post by vish garg on 2014-10-24
I'll try thanks for the help :)
I've destroyed the environment because I was not able to find solution or support.

---

### Post by Slaan on 2014-12-21
Hi !
I got exactly the same problems. Install openstack on two node with MAAS and JUJU.
Did you find the issue ?
Thx.

---

### Post by Slaan on 2014-12-21
Ok, it seem ok. My instance is in 'build'

---


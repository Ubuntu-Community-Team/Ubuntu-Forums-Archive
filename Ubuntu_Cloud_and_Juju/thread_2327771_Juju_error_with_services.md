---
title: "Juju error with services"
date: 2016-06-14
forum: Ubuntu Cloud and Juju
---

### Post by tzoun on 2016-06-14
Hello, I have a local set up of openstack using maas-juju-openstack.

I got error from 2 services --> hook failed: "update-status"
The error log from the machine-lxc has these errors: > error dialing "wss://192.168.101.6:17070/environment/0f6d8d6f-16ad-42a0-800e-10f140fa5308/api": websocket.Dial wss://192.168.101.6:17070/environment/0f6d8d6f-16ad-42a0-800e-10f140fa5308/api: dial tcp 192.168.101.6:17070: connection refused
2016-06-13 13:21:29 INFO juju.api apiclient.go:270 error dialing "wss://192.168.101.34:17070/environment/0f6d8d6f-16ad-42a0-800e-10f140fa5308/api": websocket.Dial wss://192.168.101.34:17070/environment/0f6d8d6f-16ad-42a0-800e-10f140fa5308/api: dial tcp 192.168.101.34:17070: connection refused
2016-06-13 13:21:29 INFO juju.worker runner.go:275 stopped "api", err: unable to connect to "wss://192.168.101.34:17070/environment/0f6d8d6f-16ad-42a0-800e-10f140fa5308/api"
2016-06-13 13:21:32 INFO juju.worker runner.go:275 stopped "api", err: login for "machine-0-lxc-3" blocked because upgrade in progress
2016-06-13 13:21:37 INFO juju.worker runner.go:275 stopped "upgrade-steps", err: <nil>
2016-06-13 13:21:37 INFO juju.worker runner.go:275 stopped "networker", err: <nil>

Do you have any idea whats going on?

---


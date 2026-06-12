---
title: "Juju with Openstack Havan"
date: 2014-06-10
forum: Ubuntu Cloud and Juju
---

### Post by m.h.shams on 2014-06-10
Hi,

I'm trying to test Juju with my private openstack havana installation. but after bootstrap, Juju fails to communicate with vm instances, because it is trying to use private ip, instead of public one, to communicate. 

my environment and configurations are as follow: 
- an openstack havan installation, with a tenant named "demo". the tenant has a public (for floating ips) and a private network. instances with floating ip are visible to external networks and this has been tested successfully. 
- an ubuntu 12.04 (precise) image is available in openstack. 
- juju version: 1.18.4-trusty-amd64
- in the environment.yaml, use-floating-ip is true. (use-floating-ip: true)

i'm running following juju commands: 
```
juju metadata generate-image -a amd64 -i fa771718-206e-40ff-9466-c2bf8763b377 -r RegionOne -s precise -d ~/.juju/metadata -u http://openstack:5000/v2.0 -e openstack
```
```
juju metadata generate-tools -d ~/.juju/metadata
```
```
juju bootstrap --metadata-source ~/.juju/metadata --upload-tools -v
```

until here, everything is successful. but if I try 'juju status', following error is shown: 
```
ERROR state/api: websocket.Dial wss://192.168.0.2:17070/: dial tcp 192.168.0.2:17070: network is unreachable
```

the problem is that, above ip (192.168.0.2) is the private one, and of course is not reachable from my external machines. How I should tell juju to use public (floating) ip address instead?

---


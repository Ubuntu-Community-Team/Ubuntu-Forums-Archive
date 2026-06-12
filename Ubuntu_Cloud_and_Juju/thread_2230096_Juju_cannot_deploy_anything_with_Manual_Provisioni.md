---
title: "Juju cannot deploy anything with Manual Provisioning"
date: 2014-06-17
forum: Ubuntu Cloud and Juju
---

### Post by samy234 on 2014-06-17
I get this error when trying to deploy my first charm:

```
ERROR cannot upload charm to provider storage: Head http://xxxxxxxxx.cloudapp.net:8040/: dial tcp 23.97.xxx.xxx:8040: connection timed out
```


this is my juju status:
```
juju status
environment: manual
machines:
  "0":
    agent-state: started
    agent-version: 1.18.4
    dns-name: 23.97.xxx.xxx
    instance-id: 'manual:'
    series: trusty
    hardware: arch=amd64 cpu-cores=1 mem=1678M
  "11":
    agent-state: started
    agent-version: 1.18.4
    dns-name: 23.97.xxx.xxx
    instance-id: manual:xxxxxxxxx.cloudapp.net
    series: trusty
    hardware: arch=amd64 cpu-cores=1 mem=1678M
  "12":
    agent-state: started
    agent-version: 1.18.4
    dns-name: 137.116.xxx.xxx
    instance-id: manual:xxxxxxxx.cloudapp.net
    series: trusty
    hardware: arch=amd64 cpu-cores=1 mem=1678M
  "13":
    agent-state: started
    agent-version: 1.18.4
    dns-name: 23.97.xxx.xxx
    instance-id: manual:xxxxxxxxx.cloudapp.net
    series: trusty
    hardware: arch=amd64 cpu-cores=1 mem=1678M
services: {}
```


I'm running 4 virtual machines with ubuntu 14.04 on windows azure cloud service. I had to open ports 80, 8040, 17070 to get juju running and add the other machines.
(I don't want to use the azure service directly this is my test invironment i will deploy juju to other virtual machines outside azure once i got comfortable with it)
What ports does juju still need?

---

### Post by samy234 on 2014-06-17
Ok i think i figured it out. It needed these additional ports: 443, 2181, 34883,

It is now running and deployment works :-)

---


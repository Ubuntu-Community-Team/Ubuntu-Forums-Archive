---
title: "Juju “RegionOne” does not allow access to all required services"
date: 2013-12-19
forum: Ubuntu Cloud and Juju
---

### Post by surrizola2 on 2013-12-19
Hi i am trying to configure juju over openstack under Ubuntu. Successfully configure the basic authentication stuff on juju enviroment.yalm but when i try to bootstrap juju this errors stop me. Anyone can give me a tip ?


Error


```
    ERROR failed to GET object provider-state from container juju-ed085dd894094e7997f2e285ed52ca28
    caused by: cannot create service URLs
    caused by: the configured region "RegionOne" does not allow access to all required services, namely: compute, object-store
    access to these services is missing: object-store

```

Config
 


```
     openstack:
        type: openstack
        admin-secret: xxxx
        control-bucket: juju-ed085dd894094e7997f2e285ed52ca28
        auth-url: http://xxxx.11:5000/v2.0
        auth-mode: userpass
        username: xxx
        password: xxx
        tenant-name: admin
        region: RegionOne



```

---


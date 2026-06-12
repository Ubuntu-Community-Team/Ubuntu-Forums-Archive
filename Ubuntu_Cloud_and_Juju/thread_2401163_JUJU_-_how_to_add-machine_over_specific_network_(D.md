---
title: "JUJU - how to add-machine over specific network (DNS)"
date: 2018-09-14
forum: Ubuntu Cloud and Juju
---

### Post by kalle1024 on 2018-09-14
Hello

I have a MAAS setup where my provisioned machines have multiple network interfaces defined on different subnets (divided through vlans)

Example
  eno1 - static assigned IP on a subnet (1.2.3.0/24) with untagged vlan and PXE working  <-- No problem here :-)
  eno2 - unconfigured interface
  eno2.10 - static assigned IP on a subnet (10.2.3.0/24) with tagged vlan
  eno2.11 - static assigned IP on a subnet (11.2.3.0/24) with tagged vlan  
  eno2.12 - static assigned IP on a subnet (12.2.3.0/24) with tagged vlan

**HOW can I acquire and add a machine through juju and at the same time control what subnet juju will connect to the machine (i.e the DNS column in juju status output)**

I prefer to NOT do it with "juju add-machine ssh:user-ip-addr"

The reason I need to be able to control this is that when deploying OpenStack/Openvswitch in a later stage the GRE tunnels will try to communicate from the wrong subnets (and thus be blocked due to vlan tagging) if I get this wrong.

Many thanks in advance

Kalle Larsson

---

### Post by emiljacero on 2018-11-05
Hi Kalle,

When configuring neutron gateway you can add data-port and bridge-mappings. Have you tried adding these and specifying the interface you want?
Example (in a bundle config):
```

  neutron-gateway:
    annotations:
      gui-x: '0'
      gui-y: '0'
    charm: cs:neutron-gateway-254
    num_units: 1
    options:
      openstack-origin: cloud:bionic-rocky
      worker-multiplier: 0.25
      bridge-mappings: physnet1:br-data
      data-port: br-data:eno2.218

```

Best regards

---


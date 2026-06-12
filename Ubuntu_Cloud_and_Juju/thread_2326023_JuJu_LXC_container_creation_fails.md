---
title: "JuJu LXC container creation fails"
date: 2016-05-27
forum: Ubuntu Cloud and Juju
---

### Post by Eric_van_Vliet on 2016-05-27
Hi,

i've just started with JuJu and i can deploy charms only in the root containers of machines.. 

If i try to create LXC containers, very simple by doing "juju deploy cs:trusty/ubuntu --to lxc:0" it fails..

juju status shows that it couldn't retrieve the template to clone.. There 

 "0":
    agent-state: started
    agent-version: 1.25.5
    dns-name: node-0xa4.maas
    instance-id: /MAAS/api/1.0/nodes/node-2036b81c-2405-11e6-8f26-74fe482d6bbb/
    series: trusty
    containers:
      0/lxc/3:
        agent-state: error
        agent-state-info: 'failed to retrieve the template to clone: lxc container
          creation failed: juju-trusty-lxc-template'
        instance-id: pending
        series: trusty
    hardware: arch=amd64 cpu-cores=32 mem=65536M availability-zone=default
    state-server-member-status: has-vote

Any ideas where to start, i can't find in any log file where it is trying to retrieve the template from..

Eric

---

### Post by Eric_van_Vliet on 2016-05-30
Right, after I destroyed the JuJu environment and redone the bootstrap it worked.

After increasing debug levels on log i found out that the retrieval was attempted form an IP address which was assigned to the JuJu server before it was static assigned. My assumption is that it was caused by some DNS caching issue..

Anyway problem solved.

---


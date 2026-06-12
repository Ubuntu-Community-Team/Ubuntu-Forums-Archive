---
title: "fail to boot lxc container"
date: 2016-11-18
forum: Virtualisation
---

### Post by davidtuti2 on 2016-11-18
Hi 
I have ubuntu 14.04. When I'm trying to boot my container it says me:

```
lxc-start: conf.c: instantiate_veth: 3105 failed to attach 'veth0J56RG' to the bridge 'lxcbr0': No such device
lxc-start: conf.c: lxc_create_network: 3388 failed to create netdev
lxc-start: start.c: lxc_spawn: 856 failed to create the network
lxc-start: start.c: __lxc_start: 1121 failed to spawn 'clusterb2'
lxc-start: lxc_start.c: main: 341 The container failed to start.
lxc-start: lxc_start.c: main: 345 Additional information can be obtained by setting the --logfile and --logpriority options.
```

I only chanve with LXC Web Panel some settings but then I revert the chages. From that moment the container not works
Any help please?
Thanks and sorry for my English!

---


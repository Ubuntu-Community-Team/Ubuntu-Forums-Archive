---
title: "cannot unset lxdbr0 raw.dnsmasq"
date: 2018-07-07
forum: Virtualisation
---

### Post by whistl034 on 2018-07-07
I tried to setup a longer dhcp lease time for lxdbr0 dhcp clients, but the dnsmasq command line options that lxd uses are overriding my setting, and now I cannot unset the lxdbr0 raw.dnsmasq value.

```

$ lxc network show lxdbr0
config:
  ipv4.address: 192.168.134.1/24
  ipv4.nat: "true"
  ipv6.address: fd42:967b:ea7:cc90::1/64
  ipv6.nat: "true"
  raw.dnsmasq: dhcp-range=192.168.134.2,192.168.134.254,335h
description: ""
name: lxdbr0
type: bridge
used_by: []
managed: true
status: Created
locations:
- none

$ lxc network set lxdbr0 raw.dnsmasq ''

and

$ lxc network unset lxdbr0 raw.dnsmasq

have no effect

$ lxc network show lxdbr0
config:
  ipv4.address: 192.168.134.1/24
  ipv4.nat: "true"
  ipv6.address: fd42:967b:ea7:cc90::1/64
  ipv6.nat: "true"
  raw.dnsmasq: dhcp-range=192.168.134.2,192.168.134.254,335h
description: ""
name: lxdbr0
type: bridge
used_by: []
managed: true
status: Created
locations:
- none

```

Any hints?

---


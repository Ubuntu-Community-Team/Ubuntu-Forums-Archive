---
title: "dual stack static ipv4/ipv6 with nocloud datasource"
date: 2016-11-15
forum: Ubuntu Cloud and Juju
---

### Post by ghalse on 2016-11-15
Does anyone know how to dual stack IPv4/IPv6 with a nocloud data source?

I'm trying to boot a xenial lts cloud-image in VMware using a cidata ISO image as a nocloud data source for configuration. My aim is to create a VM that is dual stacked with static IPv4 and IPv6 addresses on the same network interface.

I tried putting my network configuration into meta-data as suggested in the documentation, hoping to write a correct interfaces file. My meta-data file looked like:
```
instance-id: test-instance-01
local-hostname: md-cpt-01.example.net
network-interfaces: |2
  auto ens192
  iface ens192 inet static
    address [COLOR=#000000]192.0.2.16[/COLOR]
    gateway [COLOR=#000000]192.0.2.254[/COLOR]
    netmask 255.255.255.0
    dns-nameservers 8.8.8.8
  
  iface ens192 inet6 static
    address [COLOR=#000000]2001:db8:[/COLOR]c::16
    gateway [COLOR=#000000]2001:db8[/COLOR]:c::1
    netmask 64
    dns-nameservers 2001:4860:4860::8888

```
A YAML validator suggests that should result in a valid interfaces file, and copy-and-pasting the validator output into a non-cloud VM confirms this.

However it appears the nocloud datasource actually parses and rewrites the network-interfaces section rather than writing it verbatim into /etc/network/interfaces.d/. Its parser strips comments, and certainly does not seem to understand how to have two iface blocks. Whilst I can create a functioning config if I leave out the inet6 stanza, having both in does not result in a functioning config (cloud-init aborts, leaving me unable to access the box and debug futher).

I then found this: [https://gist.github.com/Informatic/0b6b24374b54d09c77b9d25595cdbd47](https://gist.github.com/Informatic/0b6b24374b54d09c77b9d25595cdbd47) which suggested adding a network-config file to the mix. So I tried this:
```
---
version: 1
config:
 - type: physical
   name: ens192
   subnets:
    - control: auto
      type: static
      address: [COLOR=#000000]192.0.2.16[/COLOR]
      netmask: 255.255.255.0
      gateway: [COLOR=#000000]192.0.2.254[/COLOR]
      dns_nameservers:
       - 8.8.8.8
    - control: auto
      type: static
      address: [COLOR=#000000]2001:db8:[/COLOR]c::16
      netmask: 64
      gateway: [COLOR=#000000]2001:db8:[/COLOR]c::1
      dns_nameservers:
       - 2001:4860:4860::8888

```
Resulting in a cidata ISO with three files: meta-data, user-data, network-config.

Again, it I only have the IPv4 block, everything works as expected. However as soon as I add the IPv6 block, I get exactly the same results as if I'd done it in the network-interfaces stanza in meta-data.

Is there a right(tm) way to do this? And does anyone have any hints as to how I can debug further, given I cannot get into the machine and see logs?

---

### Post by ghalse on 2016-11-15
So a discussion on IRC got some logs of the problem. This is what happens with network-interfaces in meta-data:
```
2016-11-15 07:26:37,883 - util.py[WARNING]: failed stage init-local
failed run of stage init-local
------------------------------------------------------------
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/cloudinit/cmd/main.py", line 521, in status_wrapper
    ret = functor(name, args)
  File "/usr/lib/python3/dist-packages/cloudinit/cmd/main.py", line 280, in main_init
    init.apply_network_config(bring_up=bool(mode != sources.DSMODE_LOCAL))
  File "/usr/lib/python3/dist-packages/cloudinit/stages.py", line 631, in apply_network_config
    netcfg, src = self._find_networking_config()
  File "/usr/lib/python3/dist-packages/cloudinit/stages.py", line 618, in _find_networking_config
    if self.datasource and hasattr(self.datasource, 'network_config'):
  File "/usr/lib/python3/dist-packages/cloudinit/sources/DataSourceNoCloud.py", line 205, in network_config
    self._network_config = eni.convert_eni_data(self._network_eni)
  File "/usr/lib/python3/dist-packages/cloudinit/net/eni.py", line 266, in convert_eni_data
    _parse_deb_config_data(ifaces, eni_data, src_dir=None, src_path=None)
  File "/usr/lib/python3/dist-packages/cloudinit/net/eni.py", line 194, in _parse_deb_config_data
    "Re-defined in '%s'." % (iface, src_path))
cloudinit.net.ParserError: Interface ens192 can only be defined once. Re-defined in 'None'.



```

It would seem I've discovered a bug - cloudinit doesn't understand that the same interface can have two address families.

Now to figure out how to work around it :-(

---

### Post by ghalse on 2016-11-15
Okay, after many hours of playing around, I found a workaround to this. Credit goes to a colleague who came up with the idea. In the hopes that it helps someone else, this works for me:
```
[COLOR=#000000][FONT=&amp]instance-id: test-instance-01
[/FONT][/COLOR]local-hostname: md-cpt-01.example.net
network-interfaces: |2
  auto ens192
  iface ens192 inet static
    address [COLOR=#000000]192.0.2.16[/COLOR]
    gateway [COLOR=#000000]192.0.2.254[/COLOR]
    netmask 255.255.255.0
    dns-nameservers 8.8.8.8
  
  auto ens192:0
  iface ens192:0 inet6 static
    address [COLOR=#000000]2001:db8:[/COLOR]c::16
    gateway [COLOR=#000000]2001:db8[/COLOR]:c::1
    netmask 64
[COLOR=#000000][FONT=&amp]    dns-nameservers 2001:4860:4860::8888[/FONT][/COLOR]
```

Doing it this way ensures that from cloud-init's point of view, the interfaces have different names. However Xenial merges the two into ens192 and thus ifconfig looks as I'd expect - a dual stacked interface.

One caveat - there are two spaces on the blank line between the IPv4 and IPv6 blocks. This is to ensure that the YAML correctly sees it as a single block. Without those spaces, the whole thing doesn't work.

---


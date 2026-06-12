---
title: "Juju OpenStack and metadata service"
date: 2019-09-10
forum: Ubuntu Cloud and Juju
---

### Post by kingttx2 on 2019-09-10
We have a PoC to generate the proper Juju yaml file for production set for Bionic/Stein. 

Everything is coming up except for the metadata service. 
```
nova-compute/0             blocked   idle   1         10.146.134.4                                Services not running that should be: nova-api-metadata, nova-compute  neutron-openvswitch/3    active    idle             10.146.134.4                                Unit is ready
  ntp/3                    active    idle             10.146.134.4    123/udp                     chrony: Ready
nova-compute/1             blocked   idle   2         10.146.134.5                                Services not running that should be: nova-api-metadata, nova-compute
  neutron-openvswitch/4    active    idle             10.146.134.5                                Unit is ready
  ntp/4                    active    idle             10.146.134.5    123/udp                     chrony: Ready
nova-compute/2             active    idle   3         10.146.134.6                                Unit is ready
  neutron-openvswitch/1    active    idle             10.146.134.6                                Unit is ready
  ntp/1                    active    idle             10.146.134.6    123/udp                     chrony: Ready

```

Logs for the nova-api-metadata service show a lot of ECONNREFUSED messages for rabbitmq plus this tidbit:
```

2019-09-09 10:50:14.973 962136 ERROR nova oslo_config.cfg.ConfigFileValueError: Value for option url from LocationInfo(location=<Locations.user: (4, True)>, detail='/etc/nova/nova.conf') is not valid: ('host, scheme were required but missing', URIReference(scheme=None, authority=None, path=None, query=None, fragment=None), ['host', 'scheme'])

```

Metadata bits from nova.conf:
```

root@juju-93c45b-2-lxd-9:/etc/nova# grep -i metadata nova.conf
enabled_apis=osapi_compute,metadata
metadata_host = 0.0.0.0
metadata_listen_port = 8765
service_metadata_proxy = True
metadata_proxy_shared_secret = {redacted}

```

We have 'enable-local-dhcp-and-metadata: true' in the Juju yaml file.

We are running behind haproxy. 

What is our missing config here?

---

### Post by kingttx2 on 2019-09-18
I'm adding relations between all of the -cluster applications and rabbitmq-server, seeing if that helps any.

---

### Post by kingttx2 on 2019-09-18
Nope, it just broke a lot of stuff.

---

### Post by kingttx2 on 2019-09-26
I went into both, unmasked each nova-api-metadata service and started them, and that unblocked the nova-compute service. 

Is the charm not notifying those two nodes they don't need the nova-api-metadata service, or did we miss a config somewhere? 

I'm going to respin with some extra configs enabled: 
      enable-metadata-network: true
      enable-isolated-metadata: true

---


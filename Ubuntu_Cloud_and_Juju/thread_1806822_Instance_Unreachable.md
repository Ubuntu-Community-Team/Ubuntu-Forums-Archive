---
title: "Instance Unreachable"
date: 2011-07-18
forum: Ubuntu Cloud and Juju
---

### Post by yskhatib on 2011-07-18
Hello,

I've installed UEC on 4 machines. I am able to start an instance but not to reach it (neither ssh nor ping). The instance has a private IP since I do not currently have any public IPs at my disposal. The security group allows for ssh port 22 connections from my network.

The console of the instance throws this error a number of times:
```
IOError: [Errno 2] No such file or directory: '/var/lib/cloud/data/cloud-config.txt'
```

Any ideas what's gone wrong?

Cheers.

---

### Post by yskhatib on 2011-07-18
from eucalyptus.conf:
```
VNET_PUBINTERFACE="eth0"
VNET_PRIVINTERFACE="eth0"
VNET_MODE="MANAGED-NOVLAN"
VNET_DHCPDAEMON="/usr/sbin/dhcpd"
VNET_DHCPUSER="dhcpd"
VNET_ADDRSPERNET="32"
#VNET_SUBNET=""
#VNET_NETMASK=""
#VNET_DNS=""
#VNET_PUBLICIPS=""
VNET_BRIDGE="br0"

```

---

### Post by sandeepdas on 2011-09-22
Did you find any solution..?

---

### Post by yskhatib on 2011-09-22
> **sandeepdas said:**
> Did you find any solution..?
not really. i tried a different image from the store (Ubuntu 10.10) and it worked for a while then started giving the same error. i'm now using yet another image (Ubuntu 9.10) and it seems to work so far.

really annoying. i looked hard into the logs, and searched online but cannot find a real solution to this.

---

### Post by obino on 2011-09-23
Hello,

it seems that your instance is having trouble to reach the metadata service (at least that's what it looks like). The metadata service is used to retried the public key and inject it into the users's ssh credentials, thus a failure to talk to it may cause your instance to be unreachable.

Have you checked your cloud network configuration? Are there collision between the IP used by the cloud (instances) and your physical network?

cheers
graziano

---

### Post by yskhatib on 2011-09-26
thanks for your reply.

no there isn't a clash in IP address space.

---


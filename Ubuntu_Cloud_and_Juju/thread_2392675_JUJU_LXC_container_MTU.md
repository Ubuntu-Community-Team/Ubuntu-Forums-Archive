---
title: "JUJU LXC container MTU"
date: 2018-05-23
forum: Ubuntu Cloud and Juju
---

### Post by acneteng on 2018-05-23
Hello,  Can anyone point me in the direction on how I can set and preserve an MTU of 9000 on bridge interface for LXC containers.  Specifically in the openstack environment provisioned with JUJU.  Also from an educational perspective how do systems provisioned with maas and JUJU get their system settings on boot.  It appears that some files get overwritten on boot.  Hoes does one preserve setting that are not provisioned correctly from MAAS and JUJU.  According to /etc/network/interfaces.d/50-cloud-init.cfg I can create a files to preserve the network settings on a physical, how do I do this on a container.

---


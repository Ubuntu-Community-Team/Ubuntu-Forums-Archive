---
title: "Juju provider combinations?"
date: 2016-04-30
forum: Ubuntu Cloud and Juju
---

### Post by phalen on 2016-04-30
Is it possible to have juju control both lxc containers and openstack/baremetal in one setup?  for example ntp would do well in a container and shared between many bundles.  tftp server or other low traffic/specialised services come to mind as well.   where heavier services like db would need their own vm from openstack or its own machine depending on the specific need. I know its easy enough to get vm/baremetal to work together though not sure if maas will handle openstack the same as straight kvm. 

any suggestions on this are greatly appriciated.

---


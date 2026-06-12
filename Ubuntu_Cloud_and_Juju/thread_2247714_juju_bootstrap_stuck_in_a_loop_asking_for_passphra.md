---
title: "juju bootstrap stuck in a loop asking for passphrase"
date: 2014-10-09
forum: Ubuntu Cloud and Juju
---

### Post by peterwilson-69 on 2014-10-09
What's going on here? JUJU Bootstrap is stuck in a loop asking for my passphrase. I've followed the official documentation for installing MAAS and JUJU and it aint working.

 Also, are there any log files that can help discover what's going on behind the scenes? Thank you.

```
peter@openstack-server:/var/log/maas$ juju bootstrapLaunching instance
WARNING picked arbitrary tools &{1.20.9-trusty-amd64 https://streams.canonical.com/juju/tools/releases/juju-1.20.9-trusty-amd64.tgz 4e2887cac81827822b96535bbb3194634fa9636636121afe62d46f49ca81ea76 8111045}
 - /MAAS/api/1.0/nodes/node-79f1b1e2-4f61-11e4-83be-000c29f03695/
Waiting for address
Attempting to connect to e8yng.maas:22
Attempting to connect to e8yng.maas:22
Attempting to connect to 192.168.137.18:22
Enter passphrase for key '/home/peter/.ssh/id_rsa':
Enter passphrase for key '/home/peter/.ssh/id_rsa':
Enter passphrase for key '/home/peter/.ssh/id_rsa':
Enter passphrase for key '/home/peter/.ssh/id_rsa':
Enter passphrase for key '/home/peter/.ssh/id_rsa':
Enter passphrase for key '/home/peter/.ssh/id_rsa':
Enter passphrase for key '/home/peter/.ssh/id_rsa':
Enter passphrase for key '/home/peter/.ssh/id_rsa':
Enter passphrase for key '/home/peter/.ssh/id_rsa':



```

---


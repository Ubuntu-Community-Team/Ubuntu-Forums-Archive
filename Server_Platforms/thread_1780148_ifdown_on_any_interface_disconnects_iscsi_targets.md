---
title: "ifdown on any interface disconnects iscsi targets"
date: 2011-06-11
forum: Server Platforms
---

### Post by unraveled on 2011-06-11
Hello, I've run into this issue where I've set up an iscsi target, but anytime I bring up or down *any* network interface it will bring up or tear down the iscsi connection.

For example, I have four configured network interfaces, eth0-3 where eth1 is a dedicated link to our iscsi target. If I bring down eth2 I'll get:

~# ifdown eth2
 * Disconnecting iSCSI targets
   ...done.
 * Stopping iSCSI initiator service
   ...done.

Is there any way to have ifup/ifpdwn only connect/disconnect the iscsi target if it's the actual interface the connection is running on? I've tried adding the interface in /etc/iscsi/ifaces/ but that didn't seem to do anything.

This is on ubuntu 11.04 server

Thanks,
Brent

---


---
title: "Unable to live migrate"
date: 2011-09-18
forum: Virtualisation
---

### Post by wcorey on 2011-09-18
My infrastructure, until recently, did not support live migrate as there was never a common disk volume. I recently installed an ISCSI target and have kvm on two machines able to atttach to it and see a common image. Both machines have the same br0 defined and I get the same ip when I boot the image on either machine.

Here is the error I get

```
Unable to migrate guest:
 Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/migrate.py", line 457, in _async_migrate
    vm.migrate(dstconn, migrate_uri, rate, live, secure)
  File "/usr/share/virt-manager/virtManager/domain.py", line 1364, in migrate
    self._backend.migrate(destconn.vmm, flags, newname, interface, rate)
  File "/usr/lib/python2.6/dist-packages/libvirt.py", line 518, in migrate
    if ret is None:raise libvirtError('virDomainMigrate() failed', dom=self)
libvirtError: operation failed: Migration unexpectedly failed

```

I had a CentOS6 desktop and a U11.04 desktop that also would not boot. I came across a discuss that seemed to indicate using the same '127.0.0.1 address for the desktop (via the virt-manager console might be an issue as the localhost on one machine is not localhost on the other. OK, that made sense. I tried a server image. Actually I noticed that the U11.03 image would silently fail.

Here is what happens.
The main VirtManager window updates to display the title on the new server in a paused state. The Cylon eye moves back and forth for about 30 seconds then the image on both servers move to a shutdown state. However, the image has been moved to the new server as I can simply start it there but it does not auto start.

TIA.

Walt

update.. the first time I migrated the server image that is what happened
the second time, same source, same destination it did live migrate, however I could not reconnect to the session, I couldn't connect at all. Going from the second machine to the first has never worked.

---


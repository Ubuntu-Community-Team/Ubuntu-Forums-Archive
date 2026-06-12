---
title: "Openstack Havana on 12.04 LTS refuses to attach a volume to VM booted from ISO"
date: 2014-02-06
forum: Ubuntu Cloud and Juju
---

### Post by cherva on 2014-02-06
There is no problem with attaching volumes to the Cirros VM.
I created a VM and booted Ubuntu server ISO on it now it sits on user name and password... and I'm unable to attach a volume to the VM... 
From horizon it says attaching and then after a sec or two it gets back to status available... from the command line 
```
root@mitosoft:~# cinder list
+--------------------------------------+-----------+--------------+------+-------------+----------+-------------+
|                  ID                  |   Status  | Display Name | Size | Volume Type | Bootable | Attached to |
+--------------------------------------+-----------+--------------+------+-------------+----------+-------------+
| ba9b33bf-68c9-41ba-9a5c-b89f28afc72f | available |   owncloud   | 450  |     None    |  false   |             |
+--------------------------------------+-----------+--------------+------+-------------+----------+-------------+
root@mitosoft:~# nova list
+--------------------------------------+----------+---------+------------+-------------+----------------+
| ID                                   | Name     | Status  | Task State | Power State | Networks       |
+--------------------------------------+----------+---------+------------+-------------+----------------+
| ac2262d7-812b-4564-ac5a-90c2f5722e3a | OwnCloud | ACTIVE  | None       | Running     | vmnet=10.0.0.3 |
| 6bbd6d1e-5c5d-401f-984f-ff09f9f07334 | test1    | SHUTOFF | None       | Shutdown    | vmnet=10.0.0.2 |
+--------------------------------------+----------+---------+------------+-------------+----------------+
root@mitosoft:~# nova volume-attach ac2262d7-812b-4564-ac5a-90c2f5722e3a ba9b33bf-68c9-41ba-9a5c-b89f28afc72f auto
+----------+--------------------------------------+
| Property | Value                                |
+----------+--------------------------------------+
| device   | /dev/hda                             |
| serverId | ac2262d7-812b-4564-ac5a-90c2f5722e3a |
| id       | ba9b33bf-68c9-41ba-9a5c-b89f28afc72f |
| volumeId | ba9b33bf-68c9-41ba-9a5c-b89f28afc72f |
+----------+--------------------------------------+

```
And then it is not attached again.... :?
How does this attaching stuff work ? Only on cloud aware images or ?
Where to look for more detailed logs ?

```
root@mitosoft:~# cat /var/log/nova/nova-scheduler.log
2014-02-06 21:27:25.305 1029 INFO nova.scheduler.filter_scheduler [req-5e11276c-d021-42cd-a7d9-73f23ea1d463 e0477bbd0eb24e96934d29627edcf7f3 c746dbf9a120400fa11414060b76b332] Attempting to build 1 instance(s) uuids: [u'80086167-c994-4f0b-96cd-0815fcdd4d0e']
2014-02-06 21:27:25.410 1029 INFO nova.scheduler.filter_scheduler [req-5e11276c-d021-42cd-a7d9-73f23ea1d463 e0477bbd0eb24e96934d29627edcf7f3 c746dbf9a120400fa11414060b76b332] Choosing host WeighedHost [host: compute1 , weight: 6961.0] for instance 80086167-c994-4f0b-96cd-0815fcdd4d0e
2014-02-06 21:27:25.806 1029 INFO nova.openstack.common.rpc.common [req-5e11276c-d021-42cd-a7d9-73f23ea1d463 e0477bbd0eb24e96934d29627edcf7f3 c746dbf9a120400fa11414060b76b332] Connected to AMQP server on controller1 :5672
2014-02-06 21:27:36.672 1029 INFO nova.scheduler.filter_scheduler [req-5e11276c-d021-42cd-a7d9-73f23ea1d463 e0477bbd0eb24e96934d29627edcf7f3 c746dbf9a120400fa11414060b76b332] Attempting to build 1 instance(s) uuids: [u'80086167-c994-4f0b-96cd-0815fcdd4d0e']
2014-02-06 21:27:36.674 1029 ERROR nova.scheduler.filter_scheduler [req-5e11276c-d021-42cd-a7d9-73f23ea1d463 e0477bbd0eb24e96934d29627edcf7f3 c746dbf9a120400fa11414060b76b332] [instance: 80086167-c994-4f0b-96cd-0815fcdd4d0e] Error from last host: compute1  (node compute1 ): [u'Traceback (most recent call last):\n', u'  File "/usr/lib/python2.7/dist-packages/nova/compute/manager.py", line 1028, in _build_instance\n    context, instance, bdms)\n', u'  File "/usr/lib/python2.7/dist-packages/nova/compute/manager.py", line 1393, in _prep_block_device\n    instance=instance)\n', u'  File "/usr/lib/python2.7/dist-packages/nova/compute/manager.py", line 1376, in _prep_block_device\n    self._await_block_device_map_created))\n', u'  File "/usr/lib/python2.7/dist-packages/nova/virt/block_device.py", line 283, in attach_block_devices\n    block_device_mapping)\n', u'  File "/usr/lib/python2.7/dist-packages/nova/virt/block_device.py", line 246, in attach\n    db_api)\n', u'  File "/usr/lib/python2.7/dist-packages/nova/virt/block_device.py", line 153, in attach\n    volume_api.check_attach(context, volume, instance=instance)\n', u'  File "/usr/lib/python2.7/dist-packages/nova/volume/cinder.py", line 231, in check_attach\n    raise exception.InvalidVolume(reason=msg)\n', u"InvalidVolume: Invalid volume: status must be 'available'\n"]
2014-02-06 21:27:36.713 1029 WARNING nova.scheduler.driver [req-5e11276c-d021-42cd-a7d9-73f23ea1d463 e0477bbd0eb24e96934d29627edcf7f3 c746dbf9a120400fa11414060b76b332] [instance: 80086167-c994-4f0b-96cd-0815fcdd4d0e] Setting instance to ERROR state.
2014-02-06 21:29:22.569 1029 INFO nova.scheduler.filter_scheduler [req-c37d9129-c9b6-4f58-922a-0c052cf2d1dd e0477bbd0eb24e96934d29627edcf7f3 c746dbf9a120400fa11414060b76b332] Attempting to build 1 instance(s) uuids: [u'ac2262d7-812b-4564-ac5a-90c2f5722e3a']
2014-02-06 21:29:22.670 1029 INFO nova.scheduler.filter_scheduler [req-c37d9129-c9b6-4f58-922a-0c052cf2d1dd e0477bbd0eb24e96934d29627edcf7f3 c746dbf9a120400fa11414060b76b332] Choosing host WeighedHost [host: compute1 , weight: 6961.0] for instance ac2262d7-812b-4564-ac5a-90c2f5722e3a

```

---

### Post by cherva on 2014-02-07
Fixed.... The cinder node was missing the qemu-utils and sysfsutils packages.

---

### Post by esedmehmet on 2014-04-10
H&#304; cherva?
How can you fixed this problem?

---


---
title: "[Openstack] Cannot attach volume to instances"
date: 2012-08-22
forum: Ubuntu Cloud and Juju
---

### Post by galaxy5111989 on 2012-08-22
When I attache a volume to a instance, the log of nova-compute output that:

> 2012-08-20 15:00:58 DEBUG nova.rpc.amqp [-] received {u'_context_roles': [u'admin'], u'_context_request_id': u'req-93276a9b-b6eb-40c2-b2ba-25895c134c7d', u'_context_read_deleted': u'no', u'args': {u'instance_uuid': u'bda89a99-f804-4328-9a4b-bfd2a20b9da0', u'mountpoint': u'/dev/vdc', u'volume_id': u'7'}, u'_context_auth_token': '<SANITIZED>', u'_context_is_admin': True, u'_context_project_id': u'1e2db3adadea44fe97e04724798f067e', u'_context_timestamp': u'2012-08-20T08:00:58.690349', u'_context_user_id': u'fa643eb3b0f14edb901ab6143b925d09', u'method': u'attach_volume', u'_context_remote_address': u'10.30.22.110'} from (pid=12572) _safe_log /usr/lib/python2.7/dist-packages/nova/rpc/common.py:160
2012-08-20 15:00:58 DEBUG nova.rpc.amqp [req-93276a9b-b6eb-40c2-b2ba-25895c134c7d fa643eb3b0f14edb901ab6143b925d09 1e2db3adadea44fe97e04724798f067e] unpacked context: {'user_id': u'fa643eb3b0f14edb901ab6143b925d09', 'roles': [u'admin'], 'timestamp': '2012-08-20T08:00:58.690349', 'auth_token': '<SANITIZED>', 'remote_address': u'10.30.22.110', 'is_admin': True, 'request_id': u'req-93276a9b-b6eb-40c2-b2ba-25895c134c7d', 'project_id': u'1e2db3adadea44fe97e04724798f067e', 'read_deleted': u'no'} from (pid=12572) _safe_log /usr/lib/python2.7/dist-packages/nova/rpc/common.py:160
2012-08-20 15:00:58 INFO nova.compute.manager [req-93276a9b-b6eb-40c2-b2ba-25895c134c7d fa643eb3b0f14edb901ab6143b925d09 1e2db3adadea44fe97e04724798f067e] check_instance_lock: decorating: |<function attach_volume at 0x231dde8>|
2012-08-20 15:00:58 INFO nova.compute.manager [req-93276a9b-b6eb-40c2-b2ba-25895c134c7d fa643eb3b0f14edb901ab6143b925d09 1e2db3adadea44fe97e04724798f067e] check_instance_lock: arguments: |<nova.compute.manager.ComputeManager object at 0x7f6f9f4e8b90>| |<nova.rpc.amqp.RpcContext object at 0x3e26210>| |bda89a99-f804-4328-9a4b-bfd2a20b9da0|
2012-08-20 15:00:58 DEBUG nova.compute.manager [req-93276a9b-b6eb-40c2-b2ba-25895c134c7d fa643eb3b0f14edb901ab6143b925d09 1e2db3adadea44fe97e04724798f067e] instance bda89a99-f804-4328-9a4b-bfd2a20b9da0: getting locked state from (pid=12572) get_lock /usr/lib/python2.7/dist-packages/nova/compute/manager.py:1603
2012-08-20 15:00:58 INFO nova.compute.manager [req-93276a9b-b6eb-40c2-b2ba-25895c134c7d fa643eb3b0f14edb901ab6143b925d09 1e2db3adadea44fe97e04724798f067e] check_instance_lock: locked: |False|
2012-08-20 15:00:58 INFO nova.compute.manager [req-93276a9b-b6eb-40c2-b2ba-25895c134c7d fa643eb3b0f14edb901ab6143b925d09 1e2db3adadea44fe97e04724798f067e] check_instance_lock: admin: |True|
2012-08-20 15:00:58 INFO nova.compute.manager [req-93276a9b-b6eb-40c2-b2ba-25895c134c7d fa643eb3b0f14edb901ab6143b925d09 1e2db3adadea44fe97e04724798f067e] check_instance_lock: executing: |<function attach_volume at 0x231dde8>|
2012-08-20 15:00:58 AUDIT nova.compute.manager [req-93276a9b-b6eb-40c2-b2ba-25895c134c7d fa643eb3b0f14edb901ab6143b925d09 1e2db3adadea44fe97e04724798f067e] [instance: bda89a99-f804-4328-9a4b-bfd2a20b9da0] Attaching volume 7 to /dev/vdc
2012-08-20 15:00:58 DEBUG nova.rpc.amqp [req-93276a9b-b6eb-40c2-b2ba-25895c134c7d fa643eb3b0f14edb901ab6143b925d09 1e2db3adadea44fe97e04724798f067e] Making asynchronous call on volume.WT-Openstack-22 ... from (pid=12572) multicall /usr/lib/python2.7/dist-packages/nova/rpc/amqp.py:326
2012-08-20 15:00:58 DEBUG nova.rpc.amqp [req-93276a9b-b6eb-40c2-b2ba-25895c134c7d fa643eb3b0f14edb901ab6143b925d09 1e2db3adadea44fe97e04724798f067e] MSG_ID is 6c8cdaebd5b345508c11839775ab7b37 from (pid=12572) multicall /usr/lib/python2.7/dist-packages/nova/rpc/amqp.py:329
2012-08-20 15:00:59 DEBUG nova.utils [req-93276a9b-b6eb-40c2-b2ba-25895c134c7d fa643eb3b0f14edb901ab6143b925d09 1e2db3adadea44fe97e04724798f067e] Attempting to grab semaphore "connect_volume" for method "connect_volume"... from (pid=12572) inner /usr/lib/python2.7/dist-packages/nova/utils.py:927
2012-08-20 15:00:59 DEBUG nova.utils [req-93276a9b-b6eb-40c2-b2ba-25895c134c7d fa643eb3b0f14edb901ab6143b925d09 1e2db3adadea44fe97e04724798f067e] Got semaphore "connect_volume" for method "connect_volume"... from (pid=12572) inner /usr/lib/python2.7/dist-packages/nova/utils.py:931
2012-08-20 15:00:59 DEBUG nova.utils [req-93276a9b-b6eb-40c2-b2ba-25895c134c7d fa643eb3b0f14edb901ab6143b925d09 1e2db3adadea44fe97e04724798f067e] Running cmd (subprocess): sudo nova-rootwrap iscsiadm -m node -T iqn.2010-10.org.openstack:volume-00000007 -p 10.30.22.110:3260 from (pid=12572) execute /usr/lib/python2.7/dist-packages/nova/utils.py:219
2012-08-20 15:00:59 DEBUG nova.virt.libvirt.volume [req-93276a9b-b6eb-40c2-b2ba-25895c134c7d fa643eb3b0f14edb901ab6143b925d09 1e2db3adadea44fe97e04724798f067e] iscsiadm (): stdout=# BEGIN RECORD 2.0-871
node.name = iqn.2010-10.org.openstack:volume-00000007
node.tpgt = -1
node.startup = automatic
iface.hwaddress = <empty>
iface.ipaddress = <empty>
iface.iscsi_ifacename = default
iface.net_ifacename = <empty>
iface.transport_name = tcp
iface.initiatorname = <empty>
node.discovery_address = <empty>
node.discovery_port = 0
node.discovery_type = static
node.session.initial_cmdsn = 0
node.session.initial_login_retry_max = 8
node.session.xmit_thread_priority = -20
node.session.cmds_max = 128
node.session.queue_depth = 32
node.session.auth.authmethod = None
node.session.auth.username = <empty>
node.session.auth.password = <empty>
node.session.auth.username_in = <empty>
node.session.auth.password_in = <empty>
node.session.timeo.replacement_timeout = 120
node.session.err_timeo.abort_timeout = 15
node.session.err_timeo.lu_reset_timeout = 20
node.session.err_timeo.host_reset_timeout = 60
node.session.iscsi.FastAbort = Yes
node.session.iscsi.InitialR2T = No
node.session.iscsi.ImmediateData = Yes
node.session.iscsi.FirstBurstLength = 262144
node.session.iscsi.MaxBurstLength = 16776192
node.session.iscsi.DefaultTime2Retain = 0
node.session.iscsi.DefaultTime2Wait = 2
node.session.iscsi.MaxConnections = 1
node.session.iscsi.MaxOutstandingR2T = 1
node.session.iscsi.ERL = 0
node.conn[0].address = 10.30.22.110
node.conn[0].port = 3260
node.conn[0].startup = manual
node.conn[0].tcp.window_size = 524288
node.conn[0].tcp.type_of_service = 0
node.conn[0].timeo.logout_timeout = 15
node.conn[0].timeo.login_timeout = 15
node.conn[0].timeo.auth_timeout = 45
node.conn[0].timeo.noop_out_interval = 5
node.conn[0].timeo.noop_out_timeout = 5
node.conn[0].iscsi.MaxRecvDataSegmentLength = 262144
node.conn[0].iscsi.HeaderDigest = None
node.conn[0].iscsi.DataDigest = None
node.conn[0].iscsi.IFMarker = No
node.conn[0].iscsi.OFMarker = No
# END RECORD
[COLOR=#FF0040] stderr= from (pid=12572) _run_iscsiadm /usr/lib/python2.7/dist-packages/nova/virt/libvirt/volume.py:112[/COLOR]
2012-08-20 15:00:59 DEBUG nova.utils [req-93276a9b-b6eb-40c2-b2ba-25895c134c7d fa643eb3b0f14edb901ab6143b925d09 1e2db3adadea44fe97e04724798f067e] Running cmd (subprocess): sudo nova-rootwrap iscsiadm -m node -T iqn.2010-10.org.openstack:volume-00000007 -p 10.30.22.110:3260 --login from (pid=12572) execute /usr/lib/python2.7/dist-packages/nova/utils.py:219
[COLOR=#FF0040]2012-08-20 15:01:00 DEBUG nova.utils [req-93276a9b-b6eb-40c2-b2ba-25895c134c7d fa643eb3b0f14edb901ab6143b925d09 1e2db3adadea44fe97e04724798f067e] Result was 255 from (pid=12572) execute /usr/lib/python2.7/dist-packages/nova/utils.py:235
2012-08-20 15:01:00 DEBUG nova.virt.libvirt.volume [req-93276a9b-b6eb-40c2-b2ba-25895c134c7d fa643eb3b0f14edb901ab6143b925d09 1e2db3adadea44fe97e04724798f067e] iscsiadm ('--login',): stdout=Logging in to [iface: default, target: iqn.2010-10.org.openstack:volume-00000007, portal: 10.30.22.110,3260]
stderr=iscsiadm: Could not login to [iface: default, target: iqn.2010-10.org.openstack:volume-00000007, portal: 10.30.22.110,3260]:
iscsiadm: initiator reported error (19 - encountered non-retryable iSCSI login failure)
 from (pid=12572) _run_iscsiadm /usr/lib/python2.7/dist-packages/nova/virt/libvirt/volume.py:112[/COLOR]
2012-08-20 15:01:00 DEBUG nova.utils [req-93276a9b-b6eb-40c2-b2ba-25895c134c7d fa643eb3b0f14edb901ab6143b925d09 1e2db3adadea44fe97e04724798f067e] Running cmd (subprocess): sudo nova-rootwrap iscsiadm -m node -T iqn.2010-10.org.openstack:volume-00000007 -p 10.30.22.110:3260 --op update -n node.startup -v automatic from (pid=12572) execute /usr/lib/python2.7/dist-packages/nova/utils.py:219
[COLOR=#FF0040]2012-08-20 15:01:00 DEBUG nova.virt.libvirt.volume [req-93276a9b-b6eb-40c2-b2ba-25895c134c7d fa643eb3b0f14edb901ab6143b925d09 1e2db3adadea44fe97e04724798f067e] iscsiadm ('--op', 'update', '-n', 'node.startup', '-v', 'automatic'): stdout= stderr= from (pid=12572) _run_iscsiadm /usr/lib/python2.7/dist-packages/nova/virt/libvirt/volume.py:112
2012-08-20 15:01:00 WARNING nova.virt.libvirt.volume [req-93276a9b-b6eb-40c2-b2ba-25895c134c7d fa643eb3b0f14edb901ab6143b925d09 1e2db3adadea44fe97e04724798f067e] ISCSI volume not yet found at: vdc. Will rescan & retry. Try number: 0
2012-08-20 15:01:00 DEBUG nova.utils [req-93276a9b-b6eb-40c2-b2ba-25895c134c7d fa643eb3b0f14edb901ab6143b925d09 1e2db3adadea44fe97e04724798f067e] Running cmd (subprocess): sudo nova-rootwrap iscsiadm -m node -T iqn.2010-10.org.openstack:volume-00000007 -p 10.30.22.110:3260 --rescan from (pid=12572) execute /usr/lib/python2.7/dist-packages/nova/utils.py:219
2012-08-20 15:01:00 DEBUG nova.utils [req-93276a9b-b6eb-40c2-b2ba-25895c134c7d fa643eb3b0f14edb901ab6143b925d09 1e2db3adadea44fe97e04724798f067e] Result was 255 from (pid=12572) execute /usr/lib/python2.7/dist-packages/nova/utils.py:235
2012-08-20 15:01:00 ERROR nova.compute.manager [req-93276a9b-b6eb-40c2-b2ba-25895c134c7d fa643eb3b0f14edb901ab6143b925d09 1e2db3adadea44fe97e04724798f067e] [instance: bda89a99-f804-4328-9a4b-bfd2a20b9da0] Attach failed /dev/vdc, removing[/COLOR]
2012-08-20 15:01:00 TRACE nova.compute.manager [instance: bda89a99-f804-4328-9a4b-bfd2a20b9da0] Traceback (most recent call last):
2012-08-20 15:01:00 TRACE nova.compute.manager [instance: bda89a99-f804-4328-9a4b-bfd2a20b9da0] File "/usr/lib/python2.7/dist-packages/nova/compute/manager.py", line 1727, in attach_volume
2012-08-20 15:01:00 TRACE nova.compute.manager [instance: bda89a99-f804-4328-9a4b-bfd2a20b9da0] mountpoint)
2012-08-20 15:01:00 TRACE nova.compute.manager [instance: bda89a99-f804-4328-9a4b-bfd2a20b9da0] File "/usr/lib/python2.7/dist-packages/nova/exception.py", line 114, in wrapped
2012-08-20 15:01:00 TRACE nova.compute.manager [instance: bda89a99-f804-4328-9a4b-bfd2a20b9da0] return f(*args, **kw)
2012-08-20 15:01:00 TRACE nova.compute.manager [instance: bda89a99-f804-4328-9a4b-bfd2a20b9da0] File "/usr/lib/python2.7/dist-packages/nova/virt/libvirt/connection.py", line 530, in attach_volume
2012-08-20 15:01:00 TRACE nova.compute.manager [instance: bda89a99-f804-4328-9a4b-bfd2a20b9da0] mount_device)
2012-08-20 15:01:00 TRACE nova.compute.manager [instance: bda89a99-f804-4328-9a4b-bfd2a20b9da0] File "/usr/lib/python2.7/dist-packages/nova/virt/libvirt/connection.py", line 522, in volume_driver_method
2012-08-20 15:01:00 TRACE nova.compute.manager [instance: bda89a99-f804-4328-9a4b-bfd2a20b9da0] return method(connection_info, *args, **kwargs)
2012-08-20 15:01:00 TRACE nova.compute.manager [instance: bda89a99-f804-4328-9a4b-bfd2a20b9da0] File "/usr/lib/python2.7/dist-packages/nova/utils.py", line 945, in inner
2012-08-20 15:01:00 TRACE nova.compute.manager [instance: bda89a99-f804-4328-9a4b-bfd2a20b9da0] retval = f(*args, **kwargs)
2012-08-20 15:01:00 TRACE nova.compute.manager [instance: bda89a99-f804-4328-9a4b-bfd2a20b9da0] File "/usr/lib/python2.7/dist-packages/nova/virt/libvirt/volume.py", line 175, in connect_volume
2012-08-20 15:01:00 TRACE nova.compute.manager [instance: bda89a99-f804-4328-9a4b-bfd2a20b9da0] self._run_iscsiadm(iscsi_properties, ("--rescan",))
2012-08-20 15:01:00 TRACE nova.compute.manager [instance: bda89a99-f804-4328-9a4b-bfd2a20b9da0] File "/usr/lib/python2.7/dist-packages/nova/virt/libvirt/volume.py", line 110, in _run_iscsiadm
2012-08-20 15:01:00 TRACE nova.compute.manager [instance: bda89a99-f804-4328-9a4b-bfd2a20b9da0] check_exit_code=check_exit_code)
2012-08-20 15:01:00 TRACE nova.compute.manager [instance: bda89a99-f804-4328-9a4b-bfd2a20b9da0] File "/usr/lib/python2.7/dist-packages/nova/utils.py", line 242, in execute
2012-08-20 15:01:00 TRACE nova.compute.manager [instance: bda89a99-f804-4328-9a4b-bfd2a20b9da0] cmd=' '.join(cmd))
[COLOR=#FF0040]2012-08-20 15:01:00 TRACE nova.compute.manager [instance: bda89a99-f804-4328-9a4b-bfd2a20b9da0] ProcessExecutionError: Unexpected error while running command.
2012-08-20 15:01:00 TRACE nova.compute.manager [instance: bda89a99-f804-4328-9a4b-bfd2a20b9da0] Command: sudo nova-rootwrap iscsiadm -m node -T iqn.2010-10.org.openstack:volume-00000007 -p 10.30.22.110:3260 --rescan
2012-08-20 15:01:00 TRACE nova.compute.manager [instance: bda89a99-f804-4328-9a4b-bfd2a20b9da0] Exit code: 255
2012-08-20 15:01:00 TRACE nova.compute.manager [instance: bda89a99-f804-4328-9a4b-bfd2a20b9da0] Stdout: ''
2012-08-20 15:01:00 TRACE nova.compute.manager [instance: bda89a99-f804-4328-9a4b-bfd2a20b9da0] Stderr: 'iscsiadm: No portal found.\n'[/COLOR]
2012-08-20 15:01:00 TRACE nova.compute.manager [instance: bda89a99-f804-4328-9a4b-bfd2a20b9da0]
2012-08-20 15:01:00 DEBUG nova.rpc.amqp [req-93276a9b-b6eb-40c2-b2ba-25895c134c7d fa643eb3b0f14edb901ab6143b925d09 1e2db3adadea44fe97e04724798f067e] Making asynchronous call on volume.WT-Openstack-22 ... from (pid=12572) multicall /usr/lib/python2.7/dist-packages/nova/rpc/amqp.py:326
2012-08-20 15:01:00 DEBUG nova.rpc.amqp [req-93276a9b-b6eb-40c2-b2ba-25895c134c7d fa643eb3b0f14edb901ab6143b925d09 1e2db3adadea44fe97e04724798f067e] MSG_ID is a336218785174eb4aa2c46b7a57aac0f from (pid=12572) multicall /usr/lib/python2.7/dist-packages/nova/rpc/amqp.py:329
[COLOR=#FF0040]2012-08-20 15:01:00 ERROR nova.rpc.amqp [req-93276a9b-b6eb-40c2-b2ba-25895c134c7d fa643eb3b0f14edb901ab6143b925d09 1e2db3adadea44fe97e04724798f067e] Exception during message handling[/COLOR]
2012-08-20 15:01:00 TRACE nova.rpc.amqp Traceback (most recent call last):
2012-08-20 15:01:00 TRACE nova.rpc.amqp File "/usr/lib/python2.7/dist-packages/nova/rpc/amqp.py", line 253, in _process_data
2012-08-20 15:01:00 TRACE nova.rpc.amqp rval = node_func(context=ctxt, **node_args)
2012-08-20 15:01:00 TRACE nova.rpc.amqp File "/usr/lib/python2.7/dist-packages/nova/exception.py", line 114, in wrapped
2012-08-20 15:01:00 TRACE nova.rpc.amqp return f(*args, **kw)
2012-08-20 15:01:00 TRACE nova.rpc.amqp File "/usr/lib/python2.7/dist-packages/nova/compute/manager.py", line 159, in decorated_function
2012-08-20 15:01:00 TRACE nova.rpc.amqp function(self, context, instance_uuid, *args, **kwargs)
2012-08-20 15:01:00 TRACE nova.rpc.amqp File "/usr/lib/python2.7/dist-packages/nova/compute/manager.py", line 183, in decorated_function
2012-08-20 15:01:00 TRACE nova.rpc.amqp sys.exc_info())
2012-08-20 15:01:00 TRACE nova.rpc.amqp File "/usr/lib/python2.7/contextlib.py", line 24, in __exit__
2012-08-20 15:01:00 TRACE nova.rpc.amqp self.gen.next()
2012-08-20 15:01:00 TRACE nova.rpc.amqp File "/usr/lib/python2.7/dist-packages/nova/compute/manager.py", line 177, in decorated_function
2012-08-20 15:01:00 TRACE nova.rpc.amqp return function(self, context, instance_uuid, *args, **kwargs)
2012-08-20 15:01:00 TRACE nova.rpc.amqp File "/usr/lib/python2.7/dist-packages/nova/compute/manager.py", line 1735, in attach_volume
2012-08-20 15:01:00 TRACE nova.rpc.amqp connector)
2012-08-20 15:01:00 TRACE nova.rpc.amqp File "/usr/lib/python2.7/contextlib.py", line 24, in __exit__
2012-08-20 15:01:00 TRACE nova.rpc.amqp self.gen.next()
2012-08-20 15:01:00 TRACE nova.rpc.amqp File "/usr/lib/python2.7/dist-packages/nova/compute/manager.py", line 1727, in attach_volume
2012-08-20 15:01:00 TRACE nova.rpc.amqp mountpoint)
2012-08-20 15:01:00 TRACE nova.rpc.amqp File "/usr/lib/python2.7/dist-packages/nova/exception.py", line 114, in wrapped
2012-08-20 15:01:00 TRACE nova.rpc.amqp return f(*args, **kw)
2012-08-20 15:01:00 TRACE nova.rpc.amqp File "/usr/lib/python2.7/dist-packages/nova/virt/libvirt/connection.py", line 530, in attach_volume
2012-08-20 15:01:00 TRACE nova.rpc.amqp mount_device)
2012-08-20 15:01:00 TRACE nova.rpc.amqp File "/usr/lib/python2.7/dist-packages/nova/virt/libvirt/connection.py", line 522, in volume_driver_method
2012-08-20 15:01:00 TRACE nova.rpc.amqp return method(connection_info, *args, **kwargs)
2012-08-20 15:01:00 TRACE nova.rpc.amqp File "/usr/lib/python2.7/dist-packages/nova/utils.py", line 945, in inner
2012-08-20 15:01:00 TRACE nova.rpc.amqp retval = f(*args, **kwargs)
2012-08-20 15:01:00 TRACE nova.rpc.amqp File "/usr/lib/python2.7/dist-packages/nova/virt/libvirt/volume.py", line 175, in connect_volume
2012-08-20 15:01:00 TRACE nova.rpc.amqp self._run_iscsiadm(iscsi_properties, ("--rescan",))
2012-08-20 15:01:00 TRACE nova.rpc.amqp File "/usr/lib/python2.7/dist-packages/nova/virt/libvirt/volume.py", line 110, in _run_iscsiadm
2012-08-20 15:01:00 TRACE nova.rpc.amqp check_exit_code=check_exit_code)
2012-08-20 15:01:00 TRACE nova.rpc.amqp File "/usr/lib/python2.7/dist-packages/nova/utils.py", line 242, in execute
2012-08-20 15:01:00 TRACE nova.rpc.amqp cmd=' '.join(cmd))
[COLOR=#FF0040]2012-08-20 15:01:00 TRACE nova.rpc.amqp ProcessExecutionError: Unexpected error while running command.
2012-08-20 15:01:00 TRACE nova.rpc.amqp Command: sudo nova-rootwrap iscsiadm -m node -T iqn.2010-10.org.openstack:volume-00000007 -p 10.30.22.110:3260 --rescan
2012-08-20 15:01:00 TRACE nova.rpc.amqp Exit code: 255
2012-08-20 15:01:00 TRACE nova.rpc.amqp Stdout: ''
2012-08-20 15:01:00 TRACE nova.rpc.amqp Stderr: 'iscsiadm: No portal found.\n'
2012-08-20 15:01:00 TRACE nova.rpc.amqp[/COLOR][COLOR=#FF0040]
[/COLOR]
And in the /var/log/syslog file, I have the error:
> Aug 20 15:01:00 WT-Openstack-22 kernel: [447693.534400] scsi29 : iSCSI Initiator over TCP/IP
Aug 20 15:01:00 WT-Openstack-22 kernel: [447693.538555] connection27:0: detected conn error (1020)
Aug 20 15:01:00 WT-Openstack-22 iscsid: conn 0 login rejected: initiator error - target not found (02/03)I have tried to fix this error for days but had no success.
I built my cloud with the following instruction: [http://docs.openstack.org/essex/openstack-compute/install/apt/content/](http://docs.openstack.org/essex/openstack-compute/install/apt/content/)
I built my cloud in an all in one node so the config for nova-volume is:
> volume_group=nova-volumes
volume_name_template=volume-%08x
iscsi_helper=tgtadm

---

### Post by galaxy5111989 on 2012-08-23
I think I just figured it:
Because I followed different  instruction, so I installed 2 packet: tgt and iscsitarget. Both of them  are packets which used to manage the connections between the iSCSI  storage subsystems in your storage area network. We must choose just one  of them. It's will catch error if we install both.

ps: I have  read a lot of article about this problem: if you install the volume node  in another host from compute node, you must have this options in  nova.conf: iscsi_ip_address={volume IP}. If not, it catch this problem  too

---

### Post by vysaboy on 2013-06-15
I got hit with the same issue and i removed [COLOR=#000000]iscsitarget and rebooted the cloud box. its now attaching the volumes. Many thanks worked !! 

However, getting below logs in compute node 
--------------------------------------------------------------------
[/COLOR]*semop up failed 22*
[I]connection1:0: detected conn error (1020)

[/I]

---


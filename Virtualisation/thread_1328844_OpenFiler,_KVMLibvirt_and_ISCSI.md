---
title: "OpenFiler, KVM/Libvirt and ISCSI"
date: 2009-11-16
forum: Virtualisation
---

### Post by xOrphenochx on 2009-11-16
Just made an OpenFiler server to mess around with. I'd like to use ISCSI in KVM as a storage pool. Having a bit of trouble adding it into virt-manager. Either the host lookup fails or login failure.

I made a simple ISCSI target with and without an incoming/outgoing chap authentication username. Anyone have a basic guide around for getting this setup?

---

### Post by xOrphenochx on 2009-11-18
I got a bit farther and now I'm stuck. Here are some details.

```
jason@Server:~/Desktop$ sudo iscsiadm -m node -L automatic -d 8
[sudo] password for jason: 
iscsiadm: Max file limits 1024 1024

iscsiadm: searching iqn.2006-01.com.openfiler:tsn.eb78e59d9777

iscsiadm: found 10.1.1.1,3260,1

iscsiadm: iface iter found default.
iscsiadm: updated 'node.name', '' => 'iqn.2006-01.com.openfiler:tsn.eb78e59d9777'
iscsiadm: updated 'node.tpgt', '-1' => '1'
iscsiadm: updated 'node.startup', 'manual' => 'automatic'
iscsiadm: updated 'iface.hwaddress', 'default' => 'default'
iscsiadm: updated 'iface.iscsi_ifacename', 'default' => 'default'
iscsiadm: updated 'iface.net_ifacename', 'default' => 'default'
iscsiadm: updated 'iface.transport_name', 'tcp' => 'tcp'
iscsiadm: updated 'node.discovery_address', '' => '10.1.1.1'
iscsiadm: updated 'node.discovery_port', '0' => '3260'
iscsiadm: updated 'node.discovery_type', 'static' => 'send_targets'
iscsiadm: updated 'node.session.initial_cmdsn', '0' => '0'
iscsiadm: updated 'node.session.initial_login_retry_max', '4' => '8'
iscsiadm: updated 'node.session.cmds_max', '128' => '128'
iscsiadm: updated 'node.session.queue_depth', '32' => '32'
iscsiadm: updated 'node.session.auth.authmethod', 'None' => 'CHAP'
iscsiadm: updated 'node.session.auth.username', '' => 'username'
iscsiadm: updated 'node.session.auth.password', '' => 'password'
iscsiadm: updated 'node.session.auth.password_length', '0' => '8'
iscsiadm: updated 'node.session.auth.username_in', '' => 'username'
iscsiadm: updated 'node.session.auth.password_in_length', '0' => '8'
iscsiadm: updated 'node.session.timeo.replacement_timeout', '120' => '120'
iscsiadm: updated 'node.session.err_timeo.abort_timeout', '15' => '15'
iscsiadm: updated 'node.session.err_timeo.lu_reset_timeout', '30' => '20'
iscsiadm: updated 'node.session.err_timeo.host_reset_timeout', '60' => '60'
iscsiadm: updated 'node.session.iscsi.FastAbort', 'Yes' => 'Yes'
iscsiadm: updated 'node.session.iscsi.InitialR2T', 'No' => 'No'
iscsiadm: updated 'node.session.iscsi.ImmediateData', 'Yes' => 'Yes'
iscsiadm: updated 'node.session.iscsi.FirstBurstLength', '262144' => '262144'
iscsiadm: updated 'node.session.iscsi.MaxBurstLength', '16776192' => '16776192'
iscsiadm: updated 'node.session.iscsi.DefaultTime2Retain', '0' => '0'
iscsiadm: updated 'node.session.iscsi.DefaultTime2Wait', '2' => '2'
iscsiadm: updated 'node.session.iscsi.MaxConnections', '1' => '1'
iscsiadm: updated 'node.session.iscsi.MaxOutstandingR2T', '1' => '1'
iscsiadm: updated 'node.session.iscsi.ERL', '0' => '0'
iscsiadm: updated 'node.conn[0].address', '' => '10.1.1.1'
iscsiadm: updated 'node.conn[0].port', '3260' => '3260'
iscsiadm: updated 'node.conn[0].startup', 'manual' => 'manual'
iscsiadm: updated 'node.conn[0].tcp.window_size', '524288' => '524288'
iscsiadm: updated 'node.conn[0].tcp.type_of_service', '0' => '0'
iscsiadm: updated 'node.conn[0].timeo.logout_timeout', '15' => '15'
iscsiadm: updated 'node.conn[0].timeo.login_timeout', '30' => '15'
iscsiadm: updated 'node.conn[0].timeo.auth_timeout', '45' => '45'
iscsiadm: updated 'node.conn[0].timeo.noop_out_interval', '5' => '5'
iscsiadm: updated 'node.conn[0].timeo.noop_out_timeout', '5' => '5'
iscsiadm: updated 'node.conn[0].iscsi.MaxRecvDataSegmentLength', '131072' => '131072'
iscsiadm: updated 'node.conn[0].iscsi.HeaderDigest', 'None' => 'None'
iscsiadm: updated 'node.conn[0].iscsi.DataDigest', 'None' => 'None'
iscsiadm: updated 'node.conn[0].iscsi.IFMarker', 'No' => 'No'
iscsiadm: updated 'node.conn[0].iscsi.OFMarker', 'No' => 'No'
iscsiadm: Could not login to [iface: default, target: iqn.2006-01.com.openfiler:tsn.eb78e59d9777, portal: 10.1.1.1,3260]: 
iscsiadm: initiator reported error (19 - encountered non-retryable iSCSI login failure)
iscsiadm: Could not log into all portals. Err 19.
jason@Server:~/Desktop$ 

```

I have the same(not included of course) credentials for CHAP for incoming and outgoing.

I have a LUN created already

---


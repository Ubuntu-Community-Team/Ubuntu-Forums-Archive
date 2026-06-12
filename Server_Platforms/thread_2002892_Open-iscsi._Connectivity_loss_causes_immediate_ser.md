---
title: "Open-iscsi. Connectivity loss causes immediate server reboot."
date: 2012-06-13
forum: Server Platforms
---

### Post by ogeen on 2012-06-13
Hi,
on Ubuntu server 12.04 I use open-iscsi, multipath-tools and ocfs2 to access shared storage HP P2000 G3 iscsi.

Even short network connectivity loss is causing immediate server crash and reboot. In syslog I can not found any clue what might hapened.

Configuration:

iscsid.conf
```
node.conn[0].startup = automatic
node.startup = automatic
node.session.timeo.replacement_timeout = 180
node.conn[0].timeo.login_timeout = 15
node.conn[0].timeo.logout_timeout = 15
node.conn[0].timeo.noop_out_interval = 5
node.conn[0].timeo.noop_out_timeout = 5
node.session.err_timeo.abort_timeout = 15
node.session.err_timeo.lu_reset_timeout = 30
node.session.initial_login_retry_max = 4
node.session.cmds_max = 128
node.session.queue_depth = 32
node.session.xmit_thread_priority = -20
node.session.iscsi.InitialR2T = No
node.session.iscsi.ImmediateData = Yes
node.session.iscsi.FirstBurstLength = 262144
node.session.iscsi.MaxBurstLength = 16776192
node.conn[0].iscsi.MaxRecvDataSegmentLength = 262144
discovery.sendtargets.iscsi.MaxRecvDataSegmentLength = 32768
node.session.iscsi.FastAbort = No
```multipath.conf:
```
defaults {
       udev_dir                /dev
       polling_interval        10
       selector                "round-robin 0"
       path_grouping_policy    multibus
       getuid_callout          "/lib/udev/scsi_id --whitelisted --device=/dev/%n"
       prio                    const
       path_checker            directio
       rr_min_io               100
       flush_on_last_del       no
       max_fds                 8192
       rr_weight               priorities
       failback                immediate
       no_path_retry           fail
       queue_without_daemon    no
       user_friendly_names     no
       mode                    644
       uid                     0
       gid                     disk
}
blacklist {
       wwid 26353900f02796769
       devnode "^(ram|raw|loop|fd|md|dm-|sr|scd|st)[0-9]*"
       devnode "^hd[a-z][[0-9]*]"
       devnode "^sda1"
       device {
               vendor DEC.*
               product MSA[15]00
       }
}
multipaths {
        multipath {
                wwid                    3600c0ff000127311ab8dcc4f01000000
        }
        multipath {
                wwid                    3600c0ff0001273712d8dcc4f01000000
        }
        multipath {
                wwid                    3600c0ff000127311cd8dcc4f01000000
        }
}
devices {
       device {
               vendor                  "HP"
               product                 "P2000 G3 FC|P2000 G3 iSCSI"
               path_grouping_policy    group_by_prio
               getuid_callout          "/lib/udev/scsi_id --whitelisted --device=/dev/%n"
               path_checker            tur
               path_selector           "round-robin 0"
               hardware_handler        "0"
               prio                    alua
               failback                immediate
               rr_weight               uniform
               no_path_retry           18
               rr_min_io               100
       }
}
```cluster.conf:
```
node:
        name = node1
        cluster = ocfs2
        number = 0
        ip_address = 192.168.1.11
        ip_port = 7777
node:
        name = node2
        cluster = ocfs2
        number = 1
        ip_address = 192.168.1.12
        ip_port = 7777
cluster:
        name = ocfs2
        node_count = 2
```How can I troubleshoot this issue? 
Thanks for any help.

---


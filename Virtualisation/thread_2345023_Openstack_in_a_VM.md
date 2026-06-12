---
title: "Openstack in a VM"
date: 2016-11-29
forum: Virtualisation
---

### Post by silver_shadow on 2016-11-29
Not sure where to post this - this "seemed" to be the appropriate sub-forum.

Anyway - I'm trying to install Openstack to learn how it works. I'm quite a noob basically. 

So my set up is - 

VM running Ubuntu 16.04
Running on VMWare Player - 1 core, 4GB RAM, 50GB disk
Using this guide to install the components one by one (all in the same VM complete with the Hypervisor - which is basically qemu/KVM which is by default) : [http://docs.openstack.org/newton/install-guide-ubuntu/index.html](http://docs.openstack.org/newton/install-guide-ubuntu/index.html)
So I've been able to install everything until the Dashboard. 

It all works except the neutron bit. Please let me know how I can trouble shoot this problem and get Neutron to work. 

And this is what's happening:
```

arjun@ubuntu:~$ . admin-openrc
arjun@ubuntu:~$ neutron ext-list
The server has either erred or is incapable of performing the requested operatio n.<br /><br />



Neutron server returns request_ids: ['req-089a756c-b35d-4512-aafb-e5757319f5dd']

```

And also tailed logs:
```

arjun@ubuntu:~$ sudo tail -f /var/log/neutron/neutron-server.log


```


A look at some of the services running:
```

arjun@ubuntu:~$ ps -ef
UID         PID   PPID  C STIME TTY          TIME CMD
root          1      0  2 19:01 ?        00:00:02 /sbin/init noprompt
root          2      0  0 19:01 ?        00:00:00 [kthreadd]
root          3      2  0 19:01 ?        00:00:00 [ksoftirqd/0]
root          4      2  0 19:01 ?        00:00:00 [kworker/0:0]
root          5      2  0 19:01 ?        00:00:00 [kworker/0:0H]
root          6      2  0 19:01 ?        00:00:00 [kworker/u256:0]
root          7      2  0 19:01 ?        00:00:00 [rcu_sched]
root          8      2  0 19:01 ?        00:00:00 [rcu_bh]
root          9      2  0 19:01 ?        00:00:00 [migration/0]
root         10      2  0 19:01 ?        00:00:00 [watchdog/0]
root         11      2  0 19:01 ?        00:00:00 [kdevtmpfs]
root         12      2  0 19:01 ?        00:00:00 [netns]
root         13      2  0 19:01 ?        00:00:00 [perf]
root         14      2  0 19:01 ?        00:00:00 [khungtaskd]
root         15      2  0 19:01 ?        00:00:00 [writeback]
root         16      2  0 19:01 ?        00:00:00 [ksmd]
root         17      2  0 19:01 ?        00:00:00 [khugepaged]
root         18      2  0 19:01 ?        00:00:00 [crypto]
root         19      2  0 19:01 ?        00:00:00 [kintegrityd]
root         20      2  0 19:01 ?        00:00:00 [bioset]
root         21      2  0 19:01 ?        00:00:00 [kblockd]
root         22      2  0 19:01 ?        00:00:00 [ata_sff]
root         23      2  0 19:01 ?        00:00:00 [md]
root         24      2  0 19:01 ?        00:00:00 [devfreq_wq]
root         25      2  0 19:01 ?        00:00:00 [kworker/u256:1]
root         26      2  0 19:01 ?        00:00:00 [kworker/0:1]
root         28      2  0 19:01 ?        00:00:00 [kswapd0]
root         29      2  0 19:01 ?        00:00:00 [vmstat]
root         30      2  0 19:01 ?        00:00:00 [fsnotify_mark]
root         31      2  0 19:01 ?        00:00:00 [ecryptfs-kthrea]
root         47      2  0 19:01 ?        00:00:00 [kthrotld]
root         48      2  0 19:01 ?        00:00:00 [acpi_thermal_pm]
root         49      2  0 19:01 ?        00:00:00 [bioset]
root         50      2  0 19:01 ?        00:00:00 [bioset]
root         51      2  0 19:01 ?        00:00:00 [bioset]
root         52      2  0 19:01 ?        00:00:00 [bioset]
root         53      2  0 19:01 ?        00:00:00 [bioset]
root         54      2  0 19:01 ?        00:00:00 [bioset]
root         55      2  0 19:01 ?        00:00:00 [bioset]
root         56      2  0 19:01 ?        00:00:00 [bioset]
root         57      2  0 19:01 ?        00:00:00 [bioset]
root         58      2  0 19:01 ?        00:00:00 [bioset]
root         59      2  0 19:01 ?        00:00:00 [bioset]
root         60      2  0 19:01 ?        00:00:00 [bioset]
root         61      2  0 19:01 ?        00:00:00 [bioset]
root         62      2  0 19:01 ?        00:00:00 [bioset]
root         63      2  0 19:01 ?        00:00:00 [bioset]
root         64      2  0 19:01 ?        00:00:00 [bioset]
root         65      2  0 19:01 ?        00:00:00 [bioset]
root         66      2  0 19:01 ?        00:00:00 [bioset]
root         67      2  0 19:01 ?        00:00:00 [bioset]
root         68      2  0 19:01 ?        00:00:00 [bioset]
root         69      2  0 19:01 ?        00:00:00 [bioset]
root         70      2  0 19:01 ?        00:00:00 [bioset]
root         71      2  0 19:01 ?        00:00:00 [bioset]
root         72      2  0 19:01 ?        00:00:00 [bioset]
root         73      2  0 19:01 ?        00:00:00 [scsi_eh_0]
root         74      2  0 19:01 ?        00:00:00 [scsi_tmf_0]
root         75      2  0 19:01 ?        00:00:00 [scsi_eh_1]
root         76      2  0 19:01 ?        00:00:00 [scsi_tmf_1]
root         77      2  0 19:01 ?        00:00:00 [kworker/u256:2]
root         81      2  0 19:01 ?        00:00:00 [ipv6_addrconf]
root         82      2  0 19:01 ?        00:00:00 [kworker/u256:3]
root         95      2  0 19:01 ?        00:00:00 [deferwq]
root         96      2  0 19:01 ?        00:00:00 [charger_manager]
root         97      2  0 19:01 ?        00:00:00 [kworker/u256:4]
root        121      2  0 19:01 ?        00:00:00 [kworker/0:2]
root        143      2  0 19:01 ?        00:00:00 [mpt_poll_0]
root        144      2  0 19:01 ?        00:00:00 [mpt/0]
root        145      2  0 19:01 ?        00:00:00 [kpsmoused]
root        146      2  0 19:01 ?        00:00:00 [scsi_eh_2]
root        147      2  0 19:01 ?        00:00:00 [scsi_tmf_2]
root        148      2  0 19:01 ?        00:00:00 [bioset]
root        150      2  0 19:01 ?        00:00:00 [ttm_swap]
root        166      2  0 19:01 ?        00:00:00 [scsi_eh_3]
root        167      2  0 19:01 ?        00:00:00 [scsi_tmf_3]
root        168      2  0 19:01 ?        00:00:00 [scsi_eh_4]
root        169      2  0 19:01 ?        00:00:00 [scsi_tmf_4]
root        170      2  0 19:01 ?        00:00:00 [scsi_eh_5]
root        171      2  0 19:01 ?        00:00:00 [scsi_tmf_5]
root        172      2  0 19:01 ?        00:00:00 [scsi_eh_6]
root        173      2  0 19:01 ?        00:00:00 [scsi_tmf_6]
root        174      2  0 19:01 ?        00:00:00 [scsi_eh_7]
root        175      2  0 19:01 ?        00:00:00 [scsi_tmf_7]
root        176      2  0 19:01 ?        00:00:00 [scsi_eh_8]
root        177      2  0 19:01 ?        00:00:00 [scsi_tmf_8]
root        178      2  0 19:01 ?        00:00:00 [scsi_eh_9]
root        179      2  0 19:01 ?        00:00:00 [scsi_tmf_9]
root        180      2  0 19:01 ?        00:00:00 [scsi_eh_10]
root        181      2  0 19:01 ?        00:00:00 [scsi_tmf_10]
root        182      2  0 19:01 ?        00:00:00 [scsi_eh_11]
root        183      2  0 19:01 ?        00:00:00 [scsi_tmf_11]
root        184      2  0 19:01 ?        00:00:00 [scsi_eh_12]
root        185      2  0 19:01 ?        00:00:00 [scsi_tmf_12]
root        186      2  0 19:01 ?        00:00:00 [scsi_eh_13]
root        187      2  0 19:01 ?        00:00:00 [scsi_tmf_13]
root        188      2  0 19:01 ?        00:00:00 [scsi_eh_14]
root        189      2  0 19:01 ?        00:00:00 [scsi_tmf_14]
root        190      2  0 19:01 ?        00:00:00 [scsi_eh_15]
root        191      2  0 19:01 ?        00:00:00 [scsi_tmf_15]
root        192      2  0 19:01 ?        00:00:00 [scsi_eh_16]
root        193      2  0 19:01 ?        00:00:00 [scsi_tmf_16]
root        194      2  0 19:01 ?        00:00:00 [scsi_eh_17]
root        195      2  0 19:01 ?        00:00:00 [scsi_tmf_17]
root        196      2  0 19:01 ?        00:00:00 [scsi_eh_18]
root        197      2  0 19:01 ?        00:00:00 [scsi_tmf_18]
root        198      2  0 19:01 ?        00:00:00 [scsi_eh_19]
root        199      2  0 19:01 ?        00:00:00 [scsi_tmf_19]
root        200      2  0 19:01 ?        00:00:00 [scsi_eh_20]
root        201      2  0 19:01 ?        00:00:00 [scsi_tmf_20]
root        202      2  0 19:01 ?        00:00:00 [scsi_eh_21]
root        203      2  0 19:01 ?        00:00:00 [scsi_tmf_21]
root        204      2  0 19:01 ?        00:00:00 [scsi_eh_22]
root        205      2  0 19:01 ?        00:00:00 [scsi_tmf_22]
root        206      2  0 19:01 ?        00:00:00 [scsi_eh_23]
root        207      2  0 19:01 ?        00:00:00 [scsi_tmf_23]
root        208      2  0 19:01 ?        00:00:00 [scsi_eh_24]
root        209      2  0 19:01 ?        00:00:00 [scsi_tmf_24]
root        210      2  0 19:01 ?        00:00:00 [scsi_eh_25]
root        211      2  0 19:01 ?        00:00:00 [scsi_tmf_25]
root        212      2  0 19:01 ?        00:00:00 [scsi_eh_26]
root        213      2  0 19:01 ?        00:00:00 [scsi_tmf_26]
root        214      2  0 19:01 ?        00:00:00 [scsi_eh_27]
root        215      2  0 19:01 ?        00:00:00 [scsi_tmf_27]
root        216      2  0 19:01 ?        00:00:00 [scsi_eh_28]
root        217      2  0 19:01 ?        00:00:00 [scsi_tmf_28]
root        218      2  0 19:01 ?        00:00:00 [scsi_eh_29]
root        219      2  0 19:01 ?        00:00:00 [scsi_tmf_29]
root        220      2  0 19:01 ?        00:00:00 [scsi_eh_30]
root        221      2  0 19:01 ?        00:00:00 [scsi_tmf_30]
root        222      2  0 19:01 ?        00:00:00 [scsi_eh_31]
root        223      2  0 19:01 ?        00:00:00 [scsi_tmf_31]
root        224      2  0 19:01 ?        00:00:00 [scsi_eh_32]
root        225      2  0 19:01 ?        00:00:00 [scsi_tmf_32]
root        226      2  0 19:01 ?        00:00:00 [kworker/u256:5]
root        227      2  0 19:01 ?        00:00:00 [kworker/u256:6]
root        228      2  0 19:01 ?        00:00:00 [kworker/u256:7]
root        229      2  0 19:01 ?        00:00:00 [kworker/u256:8]
root        230      2  0 19:01 ?        00:00:00 [kworker/u256:9]
root        231      2  0 19:01 ?        00:00:00 [kworker/u256:10]
root        232      2  0 19:01 ?        00:00:00 [kworker/u256:11]
root        233      2  0 19:01 ?        00:00:00 [kworker/u256:12]
root        234      2  0 19:01 ?        00:00:00 [kworker/u256:13]
root        235      2  0 19:01 ?        00:00:00 [kworker/u256:14]
root        236      2  0 19:01 ?        00:00:00 [kworker/u256:15]
root        237      2  0 19:01 ?        00:00:00 [kworker/u256:16]
root        238      2  0 19:01 ?        00:00:00 [kworker/u256:17]
root        239      2  0 19:01 ?        00:00:00 [kworker/u256:18]
root        240      2  0 19:01 ?        00:00:00 [kworker/u256:19]
root        241      2  0 19:01 ?        00:00:00 [kworker/u256:20]
root        242      2  0 19:01 ?        00:00:00 [kworker/u256:21]
root        243      2  0 19:01 ?        00:00:00 [kworker/u256:22]
root        244      2  0 19:01 ?        00:00:00 [kworker/u256:23]
root        245      2  0 19:01 ?        00:00:00 [kworker/u256:24]
root        246      2  0 19:01 ?        00:00:00 [kworker/u256:25]
root        247      2  0 19:01 ?        00:00:00 [kworker/u256:26]
root        248      2  0 19:01 ?        00:00:00 [kworker/u256:27]
root        249      2  0 19:01 ?        00:00:00 [kworker/u256:28]
root        250      2  0 19:01 ?        00:00:00 [kworker/u256:29]
root        251      2  0 19:01 ?        00:00:00 [kworker/u256:30]
root        252      2  0 19:01 ?        00:00:00 [kworker/u256:31]
root        253      2  0 19:01 ?        00:00:00 [bioset]
root        280      2  0 19:01 ?        00:00:00 [jbd2/sda1-8]
root        281      2  0 19:01 ?        00:00:00 [ext4-rsv-conver]
root        313      2  0 19:01 ?        00:00:00 [kworker/0:3]
root        317      2  0 19:01 ?        00:00:00 [kworker/0:1H]
root        332      1  0 19:01 ?        00:00:00 /lib/systemd/systemd-journald
root        337      2  0 19:01 ?        00:00:00 [kworker/0:4]
root        339      1  0 19:01 ?        00:00:00 vmware-vmblock-fuse /run/vmblo
root        340      2  0 19:01 ?        00:00:00 [kauditd]
root        342      2  0 19:01 ?        00:00:00 [iscsi_eh]
root        348      2  0 19:01 ?        00:00:00 [ib_addr]
root        358      2  0 19:01 ?        00:00:00 [ib_mcast]
root        361      2  0 19:01 ?        00:00:00 [ib_nl_sa_wq]
root        362      2  0 19:01 ?        00:00:00 [ib_cm]
root        363      2  0 19:01 ?        00:00:00 [iw_cm_wq]
root        364      2  0 19:01 ?        00:00:00 [rdma_cm]
root        385      1  0 19:01 ?        00:00:00 /lib/systemd/systemd-udevd
root        495      2  0 19:01 ?        00:00:00 [kvm-irqfd-clean]
root        668      1  0 19:01 ?        00:00:00 /usr/sbin/cron -f
root        669      1  0 19:01 ?        00:00:00 /usr/lib/accountsservice/accou
root        670      1  0 19:01 ?        00:00:00 /usr/bin/vmtoolsd
message+    671      1  0 19:01 ?        00:00:00 /usr/bin/dbus-daemon --system
root        685      1  0 19:01 ?        00:00:00 /lib/systemd/systemd-logind
syslog      690      1  0 19:01 ?        00:00:00 /usr/sbin/rsyslogd -n
root        697      1  0 19:01 ?        00:00:00 /sbin/cgmanager -m name=system
root        749      1  0 19:01 ?        00:00:00 /bin/sh /usr/lib/apt/apt.syste
root        779      1  0 19:01 ?        00:00:00 /sbin/dhclient -1 -v -pf /run/
root        852      1  0 19:01 ?        00:00:00 /usr/sbin/sshd -D
rabbitmq    854      1  0 19:01 ?        00:00:00 /bin/sh /usr/sbin/rabbitmq-ser
memcache    860      1  0 19:01 ?        00:00:00 /usr/bin/memcached -m 64 -p 11
root        880      1  0 19:01 ?        00:00:00 /sbin/iscsid
root        881      1  0 19:01 ?        00:00:00 /sbin/iscsid
rabbitmq    887    854  0 19:01 ?        00:00:00 /bin/sh -e /usr/lib/rabbitmq/b
rabbitmq   1004      1  0 19:01 ?        00:00:00 /usr/lib/erlang/erts-7.3/bin/e
root       1049      1  0 19:01 ?        00:00:00 /usr/sbin/libvirtd
_chrony    1118      1  0 19:01 ?        00:00:00 /usr/sbin/chronyd
root       1176      1  0 19:01 tty1     00:00:00 /sbin/agetty --noclear tty1 li
root       1236      1  0 19:01 ?        00:00:00 /usr/sbin/apache2 -k start
root       1239      1  0 19:01 ?        00:00:00 /bin/bash /usr/bin/mysqld_safe
root       1240      1  0 19:01 ?        00:00:00 logger -p daemon err -t /etc/i
horizon    1242   1236  0 19:01 ?        00:00:00 (wsgi:horizon)    -k start
horizon    1243   1236  0 19:01 ?        00:00:00 (wsgi:horizon)    -k start
horizon    1244   1236  0 19:01 ?        00:00:00 (wsgi:horizon)    -k start
keystone   1245   1236  0 19:01 ?        00:00:00 (wsgi:keystone-pu -k start
keystone   1246   1236  0 19:01 ?        00:00:00 (wsgi:keystone-pu -k start
keystone   1247   1236  0 19:01 ?        00:00:00 (wsgi:keystone-pu -k start
keystone   1248   1236  0 19:01 ?        00:00:00 (wsgi:keystone-pu -k start
keystone   1255   1236  0 19:01 ?        00:00:00 (wsgi:keystone-pu -k start
keystone   1273   1236  2 19:01 ?        00:00:02 (wsgi:keystone-ad -k start
keystone   1274   1236  0 19:01 ?        00:00:00 (wsgi:keystone-ad -k start
keystone   1275   1236  0 19:01 ?        00:00:00 (wsgi:keystone-ad -k start
keystone   1287   1236  0 19:01 ?        00:00:00 (wsgi:keystone-ad -k start
keystone   1288   1236  3 19:01 ?        00:00:02 (wsgi:keystone-ad -k start
www-data   1289   1236  0 19:01 ?        00:00:00 /usr/sbin/apache2 -k start
www-data   1290   1236  0 19:01 ?        00:00:00 /usr/sbin/apache2 -k start
rabbitmq   1420    887  1 19:01 ?        00:00:01 /usr/lib/erlang/erts-7.3/bin/b
mysql      1490   1239  0 19:01 ?        00:00:00 /usr/sbin/mysqld --basedir=/us
root       1491   1239  0 19:01 ?        00:00:00 logger -t mysqld -p daemon err
nova       1848      1  4 19:01 ?        00:00:04 /usr/bin/python /usr/bin/nova-
rabbitmq   1938   1420  0 19:01 ?        00:00:00 inet_gethost 4
rabbitmq   1939   1938  0 19:01 ?        00:00:00 inet_gethost 4
root       1985      2  0 19:01 ?        00:00:00 [kworker/0:5]
nova       2048      1  5 19:01 ?        00:00:04 /usr/bin/python /usr/bin/nova-
root       2053      2  0 19:01 ?        00:00:00 [kworker/0:6]
glance     2057      1  2 19:01 ?        00:00:02 /usr/bin/python /usr/bin/glanc
nova       2061      1  5 19:01 ?        00:00:05 /usr/bin/python /usr/bin/nova-
neutron    2067      1  3 19:01 ?        00:00:03 /usr/bin/python /usr/bin/neutr
nova       2076      1  4 19:01 ?        00:00:04 /usr/bin/python /usr/bin/nova-
neutron    2085      1  3 19:01 ?        00:00:03 /usr/bin/python /usr/bin/neutr
glance     2090      1  3 19:01 ?        00:00:03 /usr/bin/python /usr/bin/glanc
neutron    2096      1  3 19:01 ?        00:00:03 /usr/bin/python /usr/bin/neutr
neutron    2104      1  3 19:01 ?        00:00:03 /usr/bin/python /usr/bin/neutr
nova       2109      1  5 19:01 ?        00:00:04 /usr/bin/python /usr/bin/nova-
nova       2185      1  2 19:01 ?        00:00:02 /usr/bin/python /usr/bin/nova-
glance     2340   2057  0 19:02 ?        00:00:00 /usr/bin/python /usr/bin/glanc
glance     2345   2090  0 19:02 ?        00:00:00 /usr/bin/python /usr/bin/glanc
neutron    2354   2096  0 19:02 ?        00:00:00 /usr/bin/python /usr/bin/neutr
neutron    2355   2096  0 19:02 ?        00:00:00 /usr/bin/python /usr/bin/neutr
neutron    2356   2096  0 19:02 ?        00:00:00 /usr/bin/python /usr/bin/neutr
neutron    2357   2096  0 19:02 ?        00:00:00 /usr/bin/python /usr/bin/neutr
nova       2391   2061  0 19:02 ?        00:00:00 /usr/bin/python /usr/bin/nova-
nova       2414   2061  0 19:02 ?        00:00:00 /usr/bin/python /usr/bin/nova-
root       2416    852  0 19:02 ?        00:00:00 sshd: arjun [priv]
arjun      2421      1  0 19:02 ?        00:00:00 /lib/systemd/systemd --user
arjun      2427   2421  0 19:02 ?        00:00:00 (sd-pam)
arjun      2445   2416  0 19:02 ?        00:00:00 sshd: arjun@pts/0
arjun      2446   2445  0 19:02 pts/0    00:00:00 -bash
root       2480    749 49 19:02 ?        00:00:13 /usr/bin/python3 /usr/bin/unat
_apt       2508   2480  0 19:03 ?        00:00:00 /usr/lib/apt/methods/http
arjun      2513   2446  0 19:03 pts/0    00:00:00 ps -ef

```

---

### Post by TheFu on 2016-11-30
Nested virtualization isn't trivial.
Until you have enough real hardware to make openstack possible, perhaps starting with devstack would make more sense?  Dual booting would make more sense, honestly.  1 vCPU, 4G of RAM? Really?  [http://marcoceppi.com/2014/06/deploying-openstack-with-just-two-machines/](http://marcoceppi.com/2014/06/deploying-openstack-with-just-two-machines/) says 2 physical nodes are the minimum.

BTW, for less than 10 physical machines, I wouldn't bother with openstack.  That's the minimum for Ubuntu's MaaS deployments, I've read. [https://www.ubuntu.com/cloud/maas](https://www.ubuntu.com/cloud/maas)

General Help? Not for a primarily desktop distro.  "Server" or "virtualization" subforums would have been better, though openstack really isn't discussed much here.

Since I only have 3 physical systems for this stuff, decided to skip full openstack and work on KVM on Sheepdog cluster storage. Thought I'd share that, but do what you must.

Which are you a noob at openstack, virtualization, Linux?  It appears that sw-RAID is being used and that isn't really a noob thing.

---

### Post by silver_shadow on 2016-12-01
I am a noob at Openstack :oops:

So with that said, what is different about running Dev stack v/s installing each of the components individually on a single node using apt-get? Is there a major difference in the code base? I'm guessing there is - just trying to understand. 

I was kind of hoping that an admin would help to move the thread to the appropriate forum - I was also getting a 403 every time I tried to post... looks like the forums have had some errors since the last time I posted years ago. :(

---

### Post by deadflowr on 2016-12-01
*Thread moved to **Ubuntu Cloud and Juju**.*

---


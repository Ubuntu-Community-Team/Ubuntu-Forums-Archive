---
title: "iscsi error: &quot;iscsiadm: No portals found&quot;"
date: 2014-10-20
forum: Server Platforms
---

### Post by edubidu on 2014-10-20
Hi,

Can someone help me with the following issue (Ubuntu Server Version 14.04 LTS):

```
iscsiadm -m discovery -t st -p 10.57.1.110
iscsiadm:**[COLOR=#ff0000] No portals found[/COLOR]**
```

ping 10.57.1.110
```
PING 10.57.1.110 (10.57.1.110) 56(84) bytes of data.
64 bytes from 10.57.1.110: icmp_seq=1 ttl=64 time=0.124 ms
```

cat /etc/iscsi/iscsid.conf
```
[...] node.startup = automatic [...]
```

cat /etc/iscsi/initiatorname.iscsi
```
InitiatorName=iqn.2014-10.ch.test:01:nas08
```
--> The name is ok

/etc/init.d/open-iscsi restart
```
 * Unmounting iscsi-backed filesystems                                                       [ OK ] 
 * Disconnecting iSCSI targets                                                                      iscsiadm: No matching sessions found
                                                                                             [ OK ]
 * Stopping iSCSI initiator service                                                          [ OK ] 
 * Starting iSCSI initiator service iscsid                                                   [ OK ] 
 * Setting up iSCSI targets                                                                         
iscsiadm: No records found
                                                                                             [ OK ]
 * Mounting network filesystems    

```

iscsiadm -m discovery

```
10.57.1.110:3260 via sendtargets
```

fdisk -l
```
Disk /dev/sda: 161.1 GB, 161058816000 bytes
255 heads, 63 sectors/track, 19580 cylinders, total 314568000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00043d7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   302006271   151002112   83  Linux
/dev/sda2       302008318   314566655     6279169    5  Extended
/dev/sda5       302008320   314566655     6279168   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 138.9 GB, 138907484160 bytes
256 heads, 63 sectors/track, 16821 cylinders, total 271303680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe74b1d7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1   271303679   135651839+  ee  GPT
```

iptables -l
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

dmesg
```
[77611.098872] Loading iSCSI transport class v2.0-870.
[  138.206918] iscsi: registered transport (tcp)
[  138.258408] iscsi: registered transport (iser)
[76594.860628] iscsi: registered transport (tcp)
[76594.882260] iscsi: registered transport (iser)
[77611.105770] iscsi: registered transport (tcp)
[77611.129868] iscsi: registered transport (iser)
```

/var/log/syslog
```
Oct 21 10:07:34 ttt iscsid: iscsid shutting down.
Oct 21 10:07:34 ttt kernel: [78562.689898] Loading iSCSI transport class v2.0-870.
Oct 21 10:07:34 ttt kernel: [78562.697508] iscsi: registered transport (tcp)
Oct 21 10:07:34 ttt kernel: [78562.718093] iscsi: registered transport (iser)
Oct 21 10:07:34 ttt iscsid: iSCSI logger with pid=1281 started!
Oct 21 10:07:35 ttt iscsid: iSCSI daemon with pid=1282 started!
```

The problem is not the target cause this Nas Server, when it was installed on Ubuntu Version 11.10 (GNU/Linux 3.0.0-32-server x86_64), accessed.

Thank you for some help!

---


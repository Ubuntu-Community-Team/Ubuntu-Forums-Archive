---
title: "Problems with  LIO ISCSI Target on Ubutnu 14.04"
date: 2015-06-11
forum: Server Platforms
---

### Post by maged2 on 2015-06-11
Hello 


I am having problems with LIO/targetcli, I cannot connect or discover targets from Windows 7 or Windows 8 initiators.
I tried both Ubutnu 14.04.1 and 14.04.2 server CD images with same error. 
I can get it to work on Centos 7 using exact same steps.


The error from dmesg: iSCSI Login negotiation failed.


These are the steps i did:




```
/> cd backstores/iblock
/backstores/iblock> create name=block1 dev=/dev/sdb1
/backstores/iblock> cd /iscsi
/iscsi> create
/iscsi> cd iqn.2003-01.org.linux-iscsi.ubuntu.x8664:sn.ae6d9a09df36/tpgt1/
/iscsi/iqn.20...a09df36/tpgt1> set attribute authentication=0
/iscsi/iqn.20...a09df36/tpgt1> cd portals/
/iscsi/iqn.20...tpgt1/portals> create 192.168.100.131
/iscsi/iqn.20...tpgt1/portals> cd ../luns
/iscsi/iqn.20...36/tpgt1/luns> create /backstores/iblock/block1
/iscsi/iqn.20...36/tpgt1/luns> cd ../acls
/iscsi/iqn.20...36/tpgt1/acls> create iqn.1991-05.com.microsoft:pc
/iscsi/iqn.20...36/tpgt1/acls> cd /
/> saveconfig

```



```
o- / .................................................................................................................. [...]
  o- backstores ....................................................................................................... [...]
  | o- fileio ............................................................................................ [0 Storage Object]
  | o- iblock ............................................................................................ [1 Storage Object]
  | | o- block1 ....................................................................................... [/dev/sdb1 activated]
  | o- pscsi ............................................................................................. [0 Storage Object]
  | o- rd_dr ............................................................................................. [0 Storage Object]
  | o- rd_mcp ............................................................................................ [0 Storage Object]
  o- ib_srpt .................................................................................................... [0 Targets]
  o- iscsi ....................................................................................................... [1 Target]
  | o- iqn.2003-01.org.linux-iscsi.ubuntu.x8664:sn.ae6d9a09df36 ..................................................... [1 TPG]
  |   o- tpgt1 .................................................................................................... [enabled]
  |     o- acls ..................................................................................................... [1 ACL]
  |     | o- iqn.1991-05.com.microsoft:pc .................................................................... [1 Mapped LUN]
  |     |   o- mapped_lun0 ...................................................................................... [lun0 (rw)]
  |     o- luns ..................................................................................................... [1 LUN]
  |     | o- lun0 ............................................................................... [iblock/block1 (/dev/sdb1)]
  |     o- portals ............................................................................................... [1 Portal]
  |       o- 192.168.100.131:3260 ....................................................................... [OK, iser disabled]
  o- loopback ................................................................................................... [0 Targets]
  o- qla2xxx .................................................................................................... [0 Targets]
  o- tcm_fc ..................................................................................................... [0 Targets]
/>exit

```

```
root@ubuntu:~# service target status
[---------------------------] TCM/ConfigFS Status [----------------------------]
\------> iblock_0
        HBA Index: 1 plugin: iblock version: v4.1.0
        \-------> block1
        Status: ACTIVATED  Max Queue Depth: 0  SectorSize: 512  HwMaxSectors: 4294967288
        iBlock device: sdb1  UDEV PATH: /dev/sdb1  readonly: 0
        Major: 8 Minor: 17  CLAIMED: IBLOCK
        udev_path: /dev/sdb1


[---------------------------] LIO-Target Status [----------------------------]
\------> iqn.2003-01.org.linux-iscsi.ubuntu.x8664:sn.ae6d9a09df36
        \-------> tpgt_1  TargetAlias: LIO Target
         TPG Status: ENABLED
         TPG Network Portals:
                 \-------> 192.168.100.131:3260
         TPG Logical Units:
                 \-------> lun_0/8884242132 -> target/core/iblock_0/block1

```

Target Engine Core ConfigFS Infrastructure v4.1.0 on Linux/x86_64 on 3.16.0-30-generic
Datera Inc. iSCSI Target v4.1.0




```
root@ubuntu:~# netstat -lnp | grep 3260
tcp        0      0 192.168.100.131:3260    0.0.0.0:*               LISTEN      
```-






```
i also tried to enable CHAP for discovery with
/iscsi> set discovery_auth enable=1
/iscsi> set discovery_auth userid=user
/iscsi> set discovery_auth password=password
```
but still get dmesg: iSCSI Login negotiation failed.


Any help much appreciated.
/Maged

---


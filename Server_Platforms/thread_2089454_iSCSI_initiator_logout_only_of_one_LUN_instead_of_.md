---
title: "iSCSI initiator: logout only of one LUN instead of all"
date: 2012-11-29
forum: Server Platforms
---

### Post by freisei on 2012-11-29
Hello,

my server connects to a storage and is logging in into 2 LUNs (lun-1 and lun-5)

```
root@permain3:/dev/disk/by-path# ls -la
insgesamt 0
drwxr-xr-x 2 root root 400 Nov 29 11:35 .
drwxr-xr-x 6 root root 120 Nov 29 11:35 ..
lrwxrwxrwx 1 root root   9 Nov 29 11:35 ip-192.168.3.9:3260-iscsi-iqn.2020-01.pp.perstor1:stor1-lun-1 -> ../../sdg
lrwxrwxrwx 1 root root  10 Nov 29 11:35 ip-192.168.3.9:3260-iscsi-iqn.2020-01.pp.perstor1:stor1-lun-1-part1 -> ../../sdg1
lrwxrwxrwx 1 root root   9 Nov 29 12:27 ip-192.168.3.9:3260-iscsi-iqn.2020-01.pp.perstor1:stor1-lun-5 -> ../../sdh
lrwxrwxrwx 1 root root  10 Nov 29 11:35 ip-192.168.3.9:3260-iscsi-iqn.2020-01.pp.perstor1:stor1-lun-5-part1 -> ../../sdh1
lrwxrwxrwx 1 root root  10 Nov 29 11:35 ip-192.168.3.9:3260-iscsi-iqn.2020-01.pp.perstor1:stor1-lun-5-part2 -> ../../sdh2

```When logging out of the target with
```
iscsiadm -m node --logout -p 192.168.3.9
``` all luns are closed.
is it possible to close only one lun? For example close lun-5 an let lun-1 open?

Sincerly Freisei

---


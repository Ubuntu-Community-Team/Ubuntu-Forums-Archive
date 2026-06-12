---
title: "volume_key ubuntu 20:04"
date: 2020-04-03
forum: Ubuntu Development Version
---

### Post by zukos on 2020-04-03
Links: 
[http://manpages.ubuntu.com/manpages/eoan/man8/volume_key.8.html](http://manpages.ubuntu.com/manpages/eoan/man8/volume_key.8.html)
[https://linux.die.net/man/8/cryptsetup](https://linux.die.net/man/8/cryptsetup)

hello 

I am trying to use volume_key on the following system


```
###############~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=20.04
DISTRIB_CODENAME=focal
DISTRIB_DESCRIPTION="Ubuntu Focal Fossa (development branch)"


###############~$ uname -a
Linux kmb-7666e3d6 5.4.0-21-generic #25-Ubuntu SMP Sat Mar 28 13:10:28 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux


###############~$ volume_key --version
volume_key 0.3.12
Copyright (C) 2009 Red Hat, Inc. All rights reserved.
This software is distributed under the GPL v.2.


This program is provided with NO WARRANTY, to the extent permitted by law.


###############~$  blkid
/dev/mapper/sda6_crypt: UUID="jWI7lR-Fktk-1wsk-iRiV-Xd7P-Qlx1-Gdw6dZ" TYPE="LVM2_member"
/dev/mapper/vgubuntu-swap_1: UUID="7924074f-7b9d-455c-8009-f9f0981761f7" TYPE="swap"
/dev/mapper/vgubuntu-root: UUID="2e393385-9dd5-43cc-9413-795e6bb551c1" TYPE="ext4"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda1: UUID="2049-44C2" TYPE="vfat" PARTUUID="cb043c72-01"
/dev/sda5: UUID="2c895714-cfb4-43f1-8647-348fde55eab3" TYPE="ext4" PARTUUID="cb043c72-05"
/dev/sda6: UUID="f35b5283-45b4-482d-ad7d-42cacb1e8740" TYPE="crypto_LUKS" PARTUUID="cb043c72-06"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"


###############~$ ls -lhart /dev/mapper/total 0
drwxr-xr-x  2 root root     120 apr  2 16:01 .
crw-------  1 root root 10, 236 apr  2 16:01 control
lrwxrwxrwx  1 root root       7 apr  2 16:01 sda6_crypt -> ../dm-0
lrwxrwxrwx  1 root root       7 apr  2 16:01 vgubuntu-root -> ../dm-1
lrwxrwxrwx  1 root root       7 apr  2 16:01 vgubuntu-swap_1 -> ../dm-2
drwxr-xr-x 19 root root    4,2K apr  3 09:52 ..


###############~$ ls -lhart /dev/disk/by-path/
total 0
drwxr-xr-x 6 root root 120 apr  2 16:01 ..
drwxr-xr-x 2 root root 160 apr  2 16:01 .
lrwxrwxrwx 1 root root   9 apr  2 16:01 pci-0000:00:0d.0-ata-1 -> ../../sda
lrwxrwxrwx 1 root root   9 apr  2 16:01 pci-0000:00:01.1-ata-2 -> ../../sr0
lrwxrwxrwx 1 root root  10 apr  2 16:01 pci-0000:00:0d.0-ata-1-part6 -> ../../sda6
lrwxrwxrwx 1 root root  10 apr  2 16:01 pci-0000:00:0d.0-ata-1-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 apr  2 16:01 pci-0000:00:0d.0-ata-1-part5 -> ../../sda5
lrwxrwxrwx 1 root root  10 apr  2 16:01 pci-0000:00:0d.0-ata-1-part1 -> ../../sda1



###############~$ ls -lhart /dev/disk/by-partuuid/
total 0
drwxr-xr-x 6 root root 120 apr  2 16:01 ..
drwxr-xr-x 2 root root 120 apr  2 16:01 .
lrwxrwxrwx 1 root root  10 apr  2 16:01 cb043c72-06 -> ../../sda6
lrwxrwxrwx 1 root root  10 apr  2 16:01 cb043c72-02 -> ../../sda2
lrwxrwxrwx 1 root root  10 apr  2 16:01 cb043c72-05 -> ../../sda5
lrwxrwxrwx 1 root root  10 apr  2 16:01 cb043c72-01 -> ../../sda1



###############~$ ls -lhart /dev/disk/by-uuid/
total 0
drwxr-xr-x 6 root root 120 apr  2 16:01 ..
drwxr-xr-x 2 root root 140 apr  2 16:01 .
lrwxrwxrwx 1 root root  10 apr  2 16:01 2e393385-9dd5-43cc-9413-795e6bb551c1 -> ../../dm-1
lrwxrwxrwx 1 root root  10 apr  2 16:01 7924074f-7b9d-455c-8009-f9f0981761f7 -> ../../dm-2
lrwxrwxrwx 1 root root  10 apr  2 16:01 f35b5283-45b4-482d-ad7d-42cacb1e8740 -> ../../sda6
lrwxrwxrwx 1 root root  10 apr  2 16:01 2c895714-cfb4-43f1-8647-348fde55eab3 -> ../../sda5
lrwxrwxrwx 1 root root  10 apr  2 16:01 2049-44C2 -> ../../sda1



###############~$ ls -lhart /dev/disk/by-id/
total 0
drwxr-xr-x 6 root root 120 apr  2 16:01 ..
drwxr-xr-x 2 root root 300 apr  2 16:01 .
lrwxrwxrwx 1 root root   9 apr  2 16:01 ata-VBOX_HARDDISK_VBbfc8ad60-24df8018 -> ../../sda
lrwxrwxrwx 1 root root   9 apr  2 16:01 ata-VBOX_CD-ROM_VB2-01700376 -> ../../sr0
lrwxrwxrwx 1 root root  10 apr  2 16:01 lvm-pv-uuid-jWI7lR-Fktk-1wsk-iRiV-Xd7P-Qlx1-Gdw6dZ -> ../../dm-0
lrwxrwxrwx 1 root root  10 apr  2 16:01 dm-uuid-CRYPT-LUKS2-f35b528345b4482dad7d42cacb1e8740-sda6_crypt -> ../../dm-0
lrwxrwxrwx 1 root root  10 apr  2 16:01 dm-name-sda6_crypt -> ../../dm-0
lrwxrwxrwx 1 root root  10 apr  2 16:01 dm-uuid-LVM-kDBMT08lH3MsksX9XO92Oj7LE2WHGNHcuf2yCE6ACiGStFPcX81s64ypghD3KncM -> ../../dm-1
lrwxrwxrwx 1 root root  10 apr  2 16:01 dm-name-vgubuntu-root -> ../../dm-1
lrwxrwxrwx 1 root root  10 apr  2 16:01 dm-uuid-LVM-kDBMT08lH3MsksX9XO92Oj7LE2WHGNHcrLTNEIoCO5yaglje16xBtZ3vposAT5Ls -> ../../dm-2
lrwxrwxrwx 1 root root  10 apr  2 16:01 dm-name-vgubuntu-swap_1 -> ../../dm-2
lrwxrwxrwx 1 root root  10 apr  2 16:01 ata-VBOX_HARDDISK_VBbfc8ad60-24df8018-part6 -> ../../sda6
lrwxrwxrwx 1 root root  10 apr  2 16:01 ata-VBOX_HARDDISK_VBbfc8ad60-24df8018-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 apr  2 16:01 ata-VBOX_HARDDISK_VBbfc8ad60-24df8018-part5 -> ../../sda5
lrwxrwxrwx 1 root root  10 apr  2 16:01 ata-VBOX_HARDDISK_VBbfc8ad60-24df8018-part1 -> ../../sda1
```





-The commands i executed are the following:


```
###############~$ sudo volume_key --save /dev/sda6 -o escrow-packet
volume_key: Error opening `/dev/sda6': Error getting information about volume `/dev/sda6': Invalid argument



###############~$ sudo volume_key --save /dev/mapper/sda6_crypt -o escrow-packet
volume_key: Error opening `/dev/mapper/sda6_crypt': Volume `/dev/mapper/sda6_crypt' has unsupported format
```



I understand the /path/to/volume should not be /dev/sda6 but i also tried different variations of the path to volume for the LUKS2_crypto device above and none of them works. what am i doing wrong please ?

thanks
zs

---

### Post by slickymaster on 2020-04-03
*Thread moved to **Ubuntu Development Version**.*

---


---
title: "How to check disk encryption LVM"
date: 2021-10-06
forum: Server Platforms
---

### Post by coppolino97 on 2021-10-06
Hi all,
There is an Ubuntu 14.04 LTS physical server.
I noted that LVM is enabled, but I am not sure that disk encryption is enabled too.

Here "lsblk" output about physical server storage. The system sees two physical disk becouse there are two raid, the first for system and application, the second one is for company data.

```

NAME                                  MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                                     8:0    0   2.7T  0 disk
&#9500;&#9472;sda1                                  8:1    0   487M  0 part /boot
&#9500;&#9472;sda2                                  8:2    0  11.2G  0 part [SWAP]
&#9500;&#9472;sda3                                  8:3    0  59.6G  0 part
&#9474; &#9500;&#9472;SysVol01-LV_root (dm-1)           252:1    0  15.3G  0 lvm  /
&#9474; &#9500;&#9472;SysVol01-LV_usr (dm-2)            252:2    0  30.5G  0 lvm  /usr
&#9474; &#9492;&#9472;SysVol01-LV_var (dm-3)            252:3    0  13.8G  0 lvm  /var
&#9500;&#9472;sda4                                  8:4    0  59.6G  0 part
&#9474; &#9492;&#9472;SysVol01-LV_home (dm-4)           252:4    0  59.6G  0 lvm  /home
&#9492;&#9472;sda5                                  8:5    0   2.6T  0 part
  &#9492;&#9472;SysVol01-LV_ServiceDisk (dm-5)    252:5    0   2.6T  0 lvm  /srv
sdb                                     8:16   0   7.3T  0 disk
&#9492;&#9472;sdb1                                  8:17   0   7.3T  0 part
  &#9492;&#9472;SysVol02-LV_ServiceUsrDisk (dm-0) 252:0    0   7.3T  0 lvm  /srvusr

```

Here there is "blkid" output. I do not see any flag about encryption. Is it correct?

```

/dev/sda1: UUID="4fa1ca4a-c04a-4f18-aab2-7ffdc766209c" TYPE="ext4"
/dev/sda2: UUID="cc35bd00-f62f-441b-8c3e-9411aad95fda" TYPE="swap"
/dev/sda3: UUID="57bCJr-9G5A-0PCC-sCFO-EbEJ-OCLI-bqwVrT" TYPE="LVM2_member"
/dev/sda4: UUID="u59uJN-GcOC-RQ5W-SimQ-t9EH-21ad-NohEFg" TYPE="LVM2_member"
/dev/sda5: UUID="Qjg94i-FdCQ-wsrI-NJ8C-c3Sg-Fzed-OGBVvi" TYPE="LVM2_member"
/dev/sdb1: UUID="A8SB8w-aaRv-zOVs-UzBb-Ye7b-jvTq-AmhWWS" TYPE="LVM2_member"
/dev/mapper/SysVol02-LV_ServiceUsrDisk: UUID="0f7518c3-a91c-4274-a3c7-4421b8622c60" TYPE="ext4"
/dev/mapper/SysVol01-LV_root: LABEL="/root" UUID="da608674-8b01-4ec7-ad54-b9fd81ac11f1" TYPE="ext4"
/dev/mapper/SysVol01-LV_usr: LABEL="/usr" UUID="055e99ea-9420-4543-b51d-47972c84e5e0" TYPE="ext4"
/dev/mapper/SysVol01-LV_var: LABEL="/var" UUID="d407ddb5-2e44-4961-a61f-da95e040b706" TYPE="ext4"
/dev/mapper/SysVol01-LV_home: UUID="c439e0da-b5f9-4159-b02a-4a8eb95cf71b" TYPE="ext4"
/dev/mapper/SysVol01-LV_ServiceDisk: UUID="96fbbe17-b478-41ec-9165-552affa0a07e" TYPE="ext4"

```

I a doubt about "(dm-XXX)" label. Do I see this label because LVM is enabled?
How can I check if encryption is enabled?

Best regards

---

### Post by TheFu on 2021-10-06
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
Regular support for 14.04 ended in 2019.  Only ESM support exists now.  [https://ubuntu.com/security/esm](https://ubuntu.com/security/esm) 

A don't see any LUKS containers above.  What sort of encryption do you think it has?  To my knowledge, only LUKS is supported.

---

### Post by sudodus on 2021-10-06
Like TheFu, I cannot see any LUKS containers. Is there a reason to think that there is encryption? In Ubuntu 14.04 LTS there were two alternatives, 'disk encryption' with LVM and LUKS, and 'encrypted home' + 'encrypted swap'.

When you boot the Ubuntu 14.04 LTS physical server, do you enter a passphrase before coming to the log in screen? If not, there is no LUKS encryption.

If you boot from another system (for example a live system in a USB drive), and mount an LVM container, can you see normal files, or can you see only a LUKS container, or can you see only ecryptfs containers in the home directory?

---

### Post by coppolino97 on 2021-10-06
Hi,
I know that it is an old machine. In this moment I can not upgrade, we will do in the future.

> A don't see any LUKS containers above.  What sort of encryption do you think it has?  To my knowledge, only LUKS is supported.
Personally I use Ubuntu server 20.04 LTS usually. It is an old release and I did not know very well so I asked in this forum.

Thanks for your help

---

### Post by QIII on 2021-10-06
Hello.

I will be a bit more direct.  14.04 is so far beyond end of life that it is not productive to ask the members of our community to spend their precious time in an attempt to help you with something that cannot be updated and is subject to any number of security issues.  Continuing to use 14.04 is a liability -- possibly a costly one.

Thread closed.

---


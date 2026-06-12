---
title: "libvirt seven guest verif slow, many disk acces"
date: 2016-01-15
forum: Virtualisation
---

### Post by isanaud on 2016-01-15
Hello,
I have problem with my VMs, that are sometime very slow.
When I run VM I have many disk acces. 
iotop show me a jbd2/dm-2-8 process that use many io (more than 50%) with only a seven VM powered on.
I didn't succeed installing drivers in my VM because of not signed driver refused.
 
Could you help me ?

Host : 
cpu Intel(R) Core(TM) i7-4790 CPU @ 3.60GHz
16 Go Ram
FakeRaid mode raid 0jbd2/dm-2-8

---

### Post by MAFoElffen on 2016-01-17
No one else has touched this so I thought I would ask some questions to may get enough info for others to jump in on this.

Just a curiousity: Is there a reason you chose to do dmraid instead of the more accepted and used mdadm for your software RAID type? And if you are using dmraid, why in a virtual guest???

As "jbd2" problems imply an issue with journaling, usually on ext4 file system. "jbd2/dm-2-8" implies that is has to do with dmraid, which was an earlier form of software RAID, that by the time of Ubuntu 10.04 LTS, Ubuntu, and many other popular Linux Distributions, choose to focus on mdadm as Linux Software RAID. dmraid was still chosen for some applications that have to do with certain hardware, and non-standard BIOS RAID, that was not commonly accepted as Hardware RAID. But your motherboard is not one of those that would lean that way. Besides, you said this was one a virtual guest(!) So yes, my curiosity. But this point in time, there is not many who know about dmraid, as it lost the popular favor about 5 years ago or so.

For instance, do not use the Boot Repair LiveCD. Yann and I discussed this, I set up a test environment for him, and I did some testing for him on his app. His wonderful collection of tools uses mdadm, as it is the current accepted standard for Linux Software RAID, as it pertains to Ubuntu. If it sees RAID members, it will try to use mdadm to read and make repair to the boot loader... which would be a problem in your case.

So to help yourself, please post the results of:
```

uname -srvm
lsb_release -a
sudo blkid
sudo fdisk -l
dpkg -l | grep dmraid
# if there is output from the last command, then the below.
# if not, then indicate so...
sudo dmsetup --version
sudo dmsetup info /dev/dm-{1,2,3,4,5} # modify these number to correspond to the numbers contained in your array
sudo dmraid -V
sudo dmraid -lv
sudo dmraid -r
sudo dmraid -s
sudo dmraid -s -siv

```

As you say this is on a Virtual Guest, you did not indicate which hypervisor you where using on your hypervisor host. Mentioning libvirt could mean KVM, but works with a few other hypervisors also. You did not indicate the file format of your virtual guest image. You did not mention what OS is running on the host, or on the guest.

As you indicated you are referring a virtual guest, also list any bios and system settings of your virtual guest, 

**dmraid** is usually just used if you are trying to read a mb formed BIOS RAID group of RAID members... which hypervisors do not really use... So I am confused by that error message from a virtual guest. Did you try to create a dmraid RAID array in virtual (You mention it in your host)? If so then it is a virtio error, If not, then there is a file system error. Either way, I am curious one this.

===================
The other ways I could read that post, is that you are using dmraid on your host, and...
(A) somehow this message is showing up on your guest?
(B) that the message is really on your host (that is running a hypervisor) and you are saying that the host gets and error like this when it runs a virtual guest?

So as you can tell by my questions, I am confused by both your error and your explanation. At least for me, your post brought up more questions, thus my curiosity. This could explain why no-one responded. Please help me understand.

---

### Post by isanaud on 2016-01-18
I was not enough clear in the description of the problem. jbd2/dm-2-8 appear on my host.
The disk access are on my host which is on the fake raid.
My guests are not configure with raid.

> 
**uname -srvm **: Linux 4.2.0-23-generic #28-Ubuntu SMP Sun Dec 27 17:47:31 UTC 2015 x86_64
lsb_release -a : Release:15.10 Codename:    wily
sudo blkid: /dev/sda: TYPE="isw_raid_member"
/dev/sdb: TYPE="isw_raid_member"
/dev/sdc1: UUID="7df64990-8ff4-4aba-af19-70beae396172" TYPE="ext4" PARTUUID="fc0c1fc7-01"
/dev/mapper/isw_bchgfgafea_Volume1p1: UUID="D18A-05CB" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="4ce98e6b-d148-4c9e-8a59-6f8b738cb00b"
/dev/mapper/isw_bchgfgafea_Volume1p2: UUID="a8f376ea-4b86-4321-a392-d3dd28cfdff7" TYPE="ext4" PARTUUID="c32433e4-6f5d-4a31-aac2-c2c602da7328"
/dev/mapper/isw_bchgfgafea_Volume1p3: UUID="78742883-f6d8-4884-a8e1-eaed15c67110" TYPE="swap" PARTUUID="86f00816-a9e4-4d21-a834-bce64ed92c98"
/dev/mapper/isw_bchgfgafea_Volume1: PTUUID="7939a28d-0c96-4157-9339-30ad04883aef" PTTYPE="gpt"

**sudo fdisk -l**
Disque /dev/sda : 1,8 TiB, 2000398934016 octets, 3907029168 secteurs
Unités : sectors of 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Périphérique Amorçage Start        Fin   Secteurs Size Id Type
/dev/sda1                 1 4294967295 4294967295   2T ee GPT

Partition 1 does not start on physical sector boundary.

Disque /dev/sdb : 1,8 TiB, 2000398934016 octets, 3907029168 secteurs
Unités : sectors of 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disque /dev/sdc : 1,8 TiB, 2000398934016 octets, 3907029168 secteurs
Unités : sectors of 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xfc0c1fc7

Périphérique Amorçage Start        Fin   Secteurs  Size Id Type
/dev/sdc1              2048 3907026943 3907024896  1,8T  7 HPFS/NTFS/exFAT

Disque /dev/mapper/isw_bchgfgafea_Volume1 : 3,7 TiB, 4000792707072 octets, 7814048256 secteurs
Unités : sectors of 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 16384 bytes / 32768 bytes
Disklabel type: gpt
Disk identifier: 7939A28D-0C96-4157-9339-30AD04883AEF

Périphérique                              Start        Fin   Secteurs  Size Type
/dev/mapper/isw_bchgfgafea_Volume1p1       2048    1050623    1048576  512M EFI System
/dev/mapper/isw_bchgfgafea_Volume1p2    1050624 7780612095 7779561472  3,6T Linux filesystem
/dev/mapper/isw_bchgfgafea_Volume1p3 7780612096 7814047743   33435648   16G Partition d'échange Linux

**sudo dmsetup --version**
Library version:   1.02.99 (2015-06-20)
Driver version:    4.33.0

**sudo dmsetup info /dev/dm-1**
Name:              isw_bchgfgafea_Volume1p1
State:             ACTIVE
Read Ahead:        256
Tables present:    LIVE
Open count:        1
Event number:      0
Major, minor:      252, 1
Number of targets: 1
UUID: part1-DMRAID-isw_bchgfgafea_Volume1

**sudo dmsetup info /dev/dm-2**
Name:              isw_bchgfgafea_Volume1p2
State:             ACTIVE
Read Ahead:        256
Tables present:    LIVE
Open count:        1
Event number:      0
Major, minor:      252, 2
Number of targets: 1
UUID: part2-DMRAID-isw_bchgfgafea_Volume1

**sudo dmsetup info /dev/dm-3**
Name:              isw_bchgfgafea_Volume1p3
State:             ACTIVE
Read Ahead:        256
Tables present:    LIVE
Open count:        2
Event number:      0
Major, minor:      252, 3
Number of targets: 1
UUID: part3-DMRAID-isw_bchgfgafea_Volume1

**sudo dmraid -V**
dmraid version:        1.0.0.rc16 (2009.09.16) shared 
dmraid library version:    1.0.0.rc16 (2009.09.16)
device-mapper version:    4.33.0

sudo dmraid -lv
INFO: supported metadata formats:
asr     : Adaptec HostRAID ASR (0,1,10)
ddf1    : SNIA DDF1 (0,1,4,5,linear)
hpt37x  : Highpoint HPT37X (S,0,1,10,01)
hpt45x  : Highpoint HPT45X (S,0,1,10)
isw     : Intel Software RAID (0,1,5,01)
jmicron : JMicron ATARAID (S,0,1)
lsi     : LSI Logic MegaRAID (0,1,10)
nvidia  : NVidia RAID (S,0,1,10,5)
pdc     : Promise FastTrack (S,0,1,10)
sil     : Silicon Image(tm) Medley(tm) (0,1,10)
via     : VIA Software RAID (S,0,1,10)
dos     : DOS partitions on SW RAIDs

**sudo dmraid -r**
/dev/sdb: isw, "isw_bchgfgafea", GROUP, ok, 3907029166 sectors, data@ 0
/dev/sda: isw, "isw_bchgfgafea", GROUP, ok, 3907029166 sectors, data@ 0

**sudo dmraid -s**
*** Group superset isw_bchgfgafea
--> Active Subset
name   : isw_bchgfgafea_Volume1
size   : 7814048256
stride : 32
type   : stripe
status : ok
subsets: 0
devs   : 2
spares : 0

**sudo dmraid  -siv**


---

### Post by MAFoElffen on 2016-01-20
Don't see anything there that would be from dmraid.

libvert works with a few different hypervisors, so what hypervisor "are" you using?

You are running 7 VM's ... How do you have them configured VM wise? What are their job's? There are some things that drag in virtual (databases, file services, disk intensive io services). What are their loads? Could you post at least a glimpse of the hosts "top" when this happens? Could you run "top" (or OS equivalent) on the guest when this is happening?

---


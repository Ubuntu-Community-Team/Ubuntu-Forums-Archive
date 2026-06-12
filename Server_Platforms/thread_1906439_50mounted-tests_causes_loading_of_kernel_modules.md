---
title: "50mounted-tests causes loading of kernel modules"
date: 2012-01-09
forum: Server Platforms
---

### Post by simonEURO on 2012-01-09
[FONT=Courier New][FONT=Verdana]I noticed this morning that the following kernel filesystem modules seemed to have loaded themselves over the weekend;
xfs
jfs
qnx4
btrfs

This seems to be caused by a cron job which calls this shell script;
[FONT=Courier New]/usr/lib/os-probes/50mounted-tests
[/FONT]
Can anyone tell me the purpose of this script and how to disable it please?


Simon


**_Logs_**
[/FONT]Jan  7 06:44:40 eurowrap-lnx2 kernel: [48521.930691] SGI XFS with ACLs,  security attributes, realtime, large block/inode numbers, no debug enabled 
Jan  7 06:44:40 eurowrap-lnx2 kernel: [48521.931635] SGI XFS Quota  Management subsystem 
Jan  7 06:44:40 eurowrap-lnx2 kernel: [48521.954747] JFS: nTxBlock =  8192, nTxLock = 65536 
Jan  7 06:44:40 eurowrap-lnx2 kernel: [48522.031752] NTFS driver 2.1.30  [Flags: R/O MODULE]. 
Jan  7 06:44:40 eurowrap-lnx2 kernel: [48522.061535] QNX4 filesystem  0.2.3 registered. 
Jan  7 06:44:40 eurowrap-lnx2 kernel: [48522.143991] Btrfs loaded 
Jan  7 06:44:43 eurowrap-lnx2 kernel: [48524.744603] audit_printk_skb: 9  callbacks suppressed 
Jan  7 06:44:43 eurowrap-lnx2 kernel: [48524.744606] type=1400  audit(1325918683.199:15): apparmor="STATUS" operation="profile_replace"  name="/sbin/dhclient" pid=9374 comm="apparmor_parser" 
Jan  7 06:44:43 eurowrap-lnx2 kernel: [48524.744679] type=1400  audit(1325918683.199:16): apparmor="STATUS" operation="profile_replace"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=9374  comm="apparmor_parser" 
Jan  7 06:44:43 eurowrap-lnx2 kernel: [48524.744736] type=1400  audit(1325918683.203:17): apparmor="STATUS" operation="profile_replace"  name="/usr/lib/connman/scripts/dhclient-script" pid=9374  comm="apparmor_parser" [/FONT]

---

### Post by Wayne_V on 2012-01-09
It's part of the grub2/os-prober package.  Search for os-prober here:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Looks like it can be turned off in /etc/defaults/grub

---

### Post by simonEURO on 2012-01-09
Thank you Wayne. 

I confirm that this system is set for unattended upgrades. 
A kernel upgrade is obviously going to force grub to run, which then checks for different file systems, which will then cause these modules to load.
Mystery over.

---


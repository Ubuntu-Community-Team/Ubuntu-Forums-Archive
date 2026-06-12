---
title: "iSCSI target not presenting itself"
date: 2011-04-14
forum: Server Platforms
---

### Post by scopedial on 2011-04-14
All of the information that I have so far indicates that creating a iSCSI target is pretty easy. 
My target doesn't want to make itself available on my network for some strange reason.
 
The particulars are as follows -
Ubuntu server 10.04 with all necessary updates
 
The following messages are found in /var/logs/messages -
 
*Apr 14 14:11:22 vlab-iscsi1 kernel: [185681.155076] iSCSI Enterprise Target Software - version 1.4.20.2*
*Apr 14 14:11:22 vlab-iscsi1 kernel: [185681.155146] iscsi_trgt: Registered io type fileio*
*Apr 14 14:11:22 vlab-iscsi1 kernel: [185681.155148] iscsi_trgt: Registered io type blockio*
*Apr 14 14:11:22 vlab-iscsi1 kernel: [185681.155149] iscsi_trgt: Registered io type nullio*
 
My target is configured in /etc/ietd.conf as follows -
 
*Target iqn.2010-04.ca.glab.iscsi1:glab-iscsi1*
 
*Lun 0 Path=/dev/glab-iscsi1/glab-share1,Type=fileio,IOMode=wb*
 
I get the following message when I attempt the coammand -
**sudo iscsiadm --mode discovery --type sendtargets --portal 127.0.0.1**
 
*iscsiadm: cannot make connection to 127.0.0.1:3260 (111)*
*iscsiadm: connection to discovery address 127.0.0.1 failed*
*iscsiadm: cannot make connection to 127.0.0.1:3260 (111)*
*iscsiadm: connection to discovery address 127.0.0.1 failed*
*iscsiadm: cannot make connection to 127.0.0.1:3260 (111)*
*iscsiadm: connection to discovery address 127.0.0.1 failed*
*iscsiadm: cannot make connection to 127.0.0.1:3260 (111)*
*iscsiadm: connection to discovery address 127.0.0.1 failed*
*iscsiadm: cannot make connection to 127.0.0.1:3260 (111)*
*iscsiadm: connection to discovery address 127.0.0.1 failed*
*iscsiadm: connection login retries (reopen_max) 5 exceeded*
*iscsiadm: Could not perform SendTargets discovery.*
 
 
Any advice is appreciated.

---


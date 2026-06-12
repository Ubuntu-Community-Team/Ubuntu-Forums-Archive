---
title: "iSCSIadm issue with Synology SAN"
date: 2016-02-22
forum: Server Platforms
---

### Post by scojopa on 2016-02-22
Cannot figure this out - Any help would be really appreciated. 

```
scott@hyper:~$ sudo service open-iscsi restart
 * Unmounting iscsi-backed filesystems                                                                                                                   [ OK ] 
 * Disconnecting iSCSI targets                                                                                                                                  iscsiadm: No matching sessions found
                                                                                                                                                         [ OK ]
 * Stopping iSCSI initiator service                                                                                                                      [ OK ] 
 * Starting iSCSI initiator service iscsid                                                                                                               [ OK ] 
 * Setting up iSCSI targets                                                                                                                                     
Logging in to [iface: default, target: iqn.2000-01.com.synology:san.target-1.cb0866b7df, portal: 192.168.5.212,3260] (multiple)
Logging in to [iface: default, target: iqn.2000-01.com.synology:san.target-1.cb0866b7df, portal: 192.168.5.214,3260] (multiple)
Logging in to [iface: default, target: iqn.2000-01.com.synology:san.target-1.cb0866b7df, portal: 192.168.5.211,3260] (multiple)
Logging in to [iface: default, target: iqn.2000-01.com.synology:san.target-1.cb0866b7df, portal: 192.168.5.213,3260] (multiple)
iscsiadm: Could not login to [iface: default, target: iqn.2000-01.com.synology:san.target-1.cb0866b7df, portal: 192.168.5.212,3260].
iscsiadm: initiator reported error (24 - iSCSI login failed due to authorization failure)
iscsiadm: Could not login to [iface: default, target: iqn.2000-01.com.synology:san.target-1.cb0866b7df, portal: 192.168.5.214,3260].
iscsiadm: initiator reported error (24 - iSCSI login failed due to authorization failure)
iscsiadm: Could not login to [iface: default, target: iqn.2000-01.com.synology:san.target-1.cb0866b7df, portal: 192.168.5.211,3260].
iscsiadm: initiator reported error (24 - iSCSI login failed due to authorization failure)
iscsiadm: Could not login to [iface: default, target: iqn.2000-01.com.synology:san.target-1.cb0866b7df, portal: 192.168.5.213,3260].
iscsiadm: initiator reported error (24 - iSCSI login failed due to authorization failure)
iscsiadm: Could not log into all portals
                                                                                                                                                         [ OK ]
 * Mounting network filesystems 

```

I have:

disabled CHAP on the synology.
tried changing the password to the target (on the target and updating /etc/scsi/iscsid.conf)
tried re-creating the target
here is output of sendtargets discovery

```
iscsiadm: authentication setup complete...
iscsiadm: sendtargets discovery to 192.168.5.211:3260 using isid 0x00023d000000
iscsiadm: resolved 192.168.5.211 to 192.168.5.211
iscsiadm: discovery timeouts: login 15, reopen_cnt 6, auth 45.
iscsiadm: connecting to 192.168.5.211:3260
iscsiadm: connected local port 40407 to 192.168.5.211:3260
iscsiadm: connected to discovery address 192.168.5.211
iscsiadm: discovery session to 192.168.5.211:3260 starting iSCSI login
iscsiadm: sending login PDU with current stage 0, next stage 0, transit 0x0, isid 0x00023d000000 exp_statsn 0
iscsiadm: >    InitiatorName=iqn.1993-08.org.debian:01:2eb135d19afd
iscsiadm: >    InitiatorAlias=hyper
iscsiadm: >    SessionType=Discovery
iscsiadm: >    AuthMethod=CHAP
iscsiadm: wrote 48 bytes of PDU header
iscsiadm: wrote 112 bytes of PDU data
iscsiadm: iscsi_login: Poll return 1


iscsiadm: read 48 bytes of PDU header
iscsiadm: read 48 PDU header bytes, opcode 0x23, dlength 67, data 0xd1dec0, max 32768
iscsiadm: read 67 bytes of PDU data
iscsiadm: read 1 pad bytes
iscsiadm: finished reading login PDU, 48 hdr, 0 ah, 67 data, 1 pad
iscsiadm: login current stage 0, next stage 0, transit 0x0
iscsiadm: >    AuthMethod=CHAP
iscsiadm: >    TargetAlias=Synology Target
iscsiadm: >    TargetPortalGroupTag=1
iscsiadm: login response status 0000
iscsiadm: sending login PDU with current stage 0, next stage 0, transit 0x0, isid 0x00023d000000 exp_statsn 1
iscsiadm: >    CHAP_A=5
iscsiadm: wrote 48 bytes of PDU header
iscsiadm: wrote 12 bytes of PDU data
iscsiadm: iscsi_login: Poll return 1


iscsiadm: read 48 bytes of PDU header
iscsiadm: read 48 PDU header bytes, opcode 0x23, dlength 0, data 0xd1dec0, max 32768
iscsiadm: login response status 0201
iscsiadm: Login failed to authenticate with target 
iscsiadm: discovery login to 192.168.5.211 rejected: initiator failed authorization


iscsiadm: disconnecting conn 0xd16de0, fd 3
iscsiadm: Could not perform SendTargets discovery: iSCSI login failed due to authorization failure

```

---

### Post by darkod on 2016-02-23
You have identical target names on 4 different hosts? Shouldn't they be unique? Or even if it's not necessary, have you tried with unique target names?

You want to connect the ubuntu server to the synology iscsi targets, right? You have 4 synology boxes?

PS. Did you try to connect to the targets from your desktop for example? To confirm it works as expected.

PPS. I don't know if the 4 targets mentioned in your post are the same unique target on a machine with 4 network cards and IPs (.211-.214) or targets with the same name on 4 different machines. Because if it's the latter you can have that. iSCSI targets need unique names:
> It is necessary for the iSCSI names to be unique within the operation              domain of the end user. However, since user operation domains can 
             potentially merge with other user operation domains, the iSCSI naming 
             mechanism has been architected to ensure world wide uniqueness. In  
             order to ensure both world wide name uniqueness iSCSI provides for 
             the use of different types of naming authority mechanisms.
[http://www.ietf.org/proceedings/52/I-D/draft-ietf-ips-iscsi-name-disc-03.txt](http://www.ietf.org/proceedings/52/I-D/draft-ietf-ips-iscsi-name-disc-03.txt)

---


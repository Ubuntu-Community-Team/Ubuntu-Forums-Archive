---
title: "Tell me about iSCSI."
date: 2021-09-07
forum: The Cafe
---

### Post by kevdog on 2021-09-07
What hardware do I need to setup iSCSI.  I believe this a protocol for sharing files and data however does it require specific hardware?

---

### Post by scorp123 on 2021-09-08
> **kevdog said:**
> I believe this a protocol for sharing files and data...  

More like providing whole raw SCSI disks over a TCP/IP network. Mainly used in Enterprise environments where e.g. a VM running a database (e.g. Oracle) needs iSCSI volumes delivered by a SAN (e.g. NetApp vFiler) to write down its DB data there; because you wouldn't want such data inside a VM snapshot (it would cause inconsistencies). Usually you'd also use 10 Gbit Ethernet for this.

[https://www.enterprisestorageforum.com/hardware/what-is-iscsi-and-how-does-it-work/]("https://www.enterprisestorageforum.com/hardware/what-is-iscsi-and-how-does-it-work/")

I don't really see any home use scenarios here. If all you want is to share files then the alternatives (e.g. SMB, SFTP or SSHFS ...) are easier and faster to setup than iSCSI Initiators, iSCSI Targets, iSCSI LUN's and what not. If you want to experiment with this anyway, Google will spit out plenty of guides, e.g. this one:

[https://www.informaticar.net/ubuntu-20-04-how-to-setup-iscsi-initiator/]("https://www.informaticar.net/ubuntu-20-04-how-to-setup-iscsi-initiator/")

---

### Post by kevdog on 2021-09-08
@scorp123

I took a look at those links you sent me.  They were actually pretty helpful.   I'm not so certain the iSCSI is only for data centers. I've built a TrueNAS system and have a small 10Gb network (Cat6a) in addition to a much large 1Gb network (Cat5e).  I've recently added 10Gb switch to the homelab as well.  Maybe I'll play around with the example as shown in your second link.  Thanks a lot for the explanation.

---


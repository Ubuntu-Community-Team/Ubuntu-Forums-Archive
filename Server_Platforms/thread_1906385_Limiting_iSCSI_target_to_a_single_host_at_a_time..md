---
title: "Limiting iSCSI target to a single host at a time."
date: 2012-01-09
forum: Server Platforms
---

### Post by Ernie99 on 2012-01-09
I just installed the Ubuntu “iscsitarget” package and got my iscsi target working perfectly. I followed the instructions at [http://www.howtoforge.com/using-iscsi-on-ubuntu-10.04-initiator-and-target](http://www.howtoforge.com/using-iscsi-on-ubuntu-10.04-initiator-and-target) and additionally had to add a DKMS module. I connected to the iscsi target using two windows 7 computers with the included iscsi initiator.

I really want to set iSCSI enterprise target to only allow one host at a time to connect to a single LUN. Since I am using the NTFS file system its really bad if I connect with two hosts simultaneously. I did set the MaxConnections setting to 1, but this seems to make no difference. Any Ideas ?

---


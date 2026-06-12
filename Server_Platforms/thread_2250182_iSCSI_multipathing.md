---
title: "iSCSI multipathing"
date: 2014-10-27
forum: Server Platforms
---

### Post by hashbangbinbash2 on 2014-10-27
Hi forum,

I have a Ubuntu 10.4 server (server A), and I need to mount two iSCSI drives (from remote servers B and C) that have been presented so as to copy some files between them. I can use iscsiadm to see these drives from server A, but they are appearing as 4 drives instead of 2 due to Multipathing. I know how to discover and mount iSCSI LUNs in the usual way using iscsiadm on Redhat/CentOS servers, but I'm not sure how to proceed on Ubuntu 10.04 using Multipathing.

There's a fair amount of information I don't have to hand at the moment that would I admit be helpful to know, but can anyone give any advise as to what I need to do in principal or generally to mount these drives using Multipathing from a Ubuntu 10.04 server? I can't find much online relating to this question with 10.4, the nearest guidance I have found is this:
[http://linux.dell.com/files/whitepapers/iSCSI_Multipathing_in_Ubuntu_Server.pdf](http://linux.dell.com/files/whitepapers/iSCSI_Multipathing_in_Ubuntu_Server.pdf)

But there are issues here in terms of patching that relate to 12.04, so there's a signifcant version gap here, I suspect things have changed significantly bewteen the two versions.

Any advise really appreciated.

---

### Post by hashbangbinbash2 on 2014-10-27
Ok I have been reading through this: [https://help.ubuntu.com/12.04/serverguide/multipath-admin-and-troubleshooting.html](https://help.ubuntu.com/12.04/serverguide/multipath-admin-and-troubleshooting.html)

I'm not seeing how to then login to the presented luns. If I see four luns presented, for instance seeing this: 

# iscsiadm -m discoverdb -t st -p ip.address -D
iqn..1
iqn..2
iqn..3
iqn..4

with iqn 1 and 2 belonging to server A, and iqn 3 and 4 belonging to server B, how do I actually log in to server A once (as a single lun with the two paths being transparent) and server B one (in the same sense)? I take it that I don't have to then log in 4 times, and if I do would that mean I'll then see 4 devises (/dev/sda, sdb, sdc and sdd for example)? I need the luns from these servers to appear as single devices, single volumes.

Advise appreciated, excuse please my noob delusions.

eta: I note the link posted here refers to 12.04, let me know if there are any differences from 10.04 I should be aware of in terms of Multipathing).

---

### Post by bab1 on 2014-10-27
> **hashbangbinbash2 said:**
> 
Advise appreciated, excuse please my noob delusions.



See if this is more appropriate: [http://caribou.kamikamamak.com/2014/09/30/iscsi-and-device-mapper-multipath-test-setup/]("http://caribou.kamikamamak.com/2014/09/30/iscsi-and-device-mapper-multipath-test-setup/")

---


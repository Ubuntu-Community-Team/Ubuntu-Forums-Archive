---
title: "server migration advice"
date: 2009-10-30
forum: Server Platforms
---

### Post by electronico_nc on 2009-10-30
Hi all,

I work on Ubuntu till Gutsy but I'm not a guru ...

Well I need to migrate an old server
(mails, www, mailman, network users backup) 
(celeron 1100Mhz, 256M RAM, 2*200G RAID1) with Hardy
to a new one 
(Core2Duo 5200, 4G RAM, 3*250G RAID5) with Jaunty

My question is about the operations order, should I :
1 Upgrade existing server to Intrepid, then Jaunty
2 rsync datas between the 2 computers

1 break the RAID1 in existing server
2 put it in new server and clone the HD to new HDs
3 upgrade to Jaunty

1 install fresh Jaunty on new server
2 rsync datas between the 2 computers

Other options are, for sure, welcome.
Thanks in advance for your time and advices.

PS : I wanted first to install the X86_64 server version on Jaunty but I'm not sure the rsync will be OK from a i386 Hardy version, so I plan to use the i386 Jaunty server.

---

### Post by mistypotato on 2009-12-27
Looking to do something similar.

Old server is failing...need to move EVERYTHING (as it is basically) to a NEW and totally different server.

Best way to do this?

---

### Post by HighCommander540 on 2009-12-27
> **mistypotato said:**
> Looking to do something similar.

Old server is failing...need to move EVERYTHING (as it is basically) to a NEW and totally different server.

Best way to do this?

Just move the hard drive to the new computer or clone the partition using a partition editor.

---

### Post by WTF_Shelley on 2009-12-27
1) back up the data
2) Check the back ups
3) back up again to another destination. ( ie out of the office )
4) check the back ups

I only mention this because only i once decided to "just eff it and get it done quick" and spent the next three days trying pulling data off a broken raid set.

I would just plug the old raid set into the new box, boot off an live cd and clone the drives to the new raid, switch off, pull the old disks and reboot. Then dist upgrade, only if the distro version you have is no longer getting security patches or you need new versions of the software.  If it works and is secure leave well alone.

---


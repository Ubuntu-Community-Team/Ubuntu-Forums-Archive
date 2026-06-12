---
title: "OCFS2 setup on 5.10"
date: 2006-03-25
forum: Server Platforms
---

### Post by lbates35476 on 2006-03-25
According to the documentation Ubuntu 5.10 should have OCFS2 integrated.  I've done new server install and there do appear to be some modules installed:

administrator@scc-backups:~$ locate ocfs2
/lib/modules/2.6.12-10-386/kernel/fs/ocfs2
/lib/modules/2.6.12-10-386/kernel/fs/ocfs2/cluster
/lib/modules/2.6.12-10-386/kernel/fs/ocfs2/cluster/ocfs2_nodemanager.ko
/lib/modules/2.6.12-10-386/kernel/fs/ocfs2/dlm
/lib/modules/2.6.12-10-386/kernel/fs/ocfs2/dlm/ocfs2_dlmfs.ko
/lib/modules/2.6.12-10-386/kernel/fs/ocfs2/dlm/ocfs2_dlm.ko

But when I try to do 

man mk2fs.ocfs2 I get "No manual entry for mkfs.ocfs".

mk2fs.ocfs2 returns "-bash: mkfs.ocfs2: command not found".

I'm missing a step here, but I can't seem to find what else needs to be
done to get this working.

Thanks in advance.

---


---
title: "NFS handles stale although NFS server is running"
date: 2010-09-12
forum: Server Platforms
---

### Post by c24ck32 on 2010-09-12
We have a HP NAS server providing storage through NFS to our Ubuntu 9.04 cluster and a few other hosts also running Ubuntu. Every few weeks or so, the cluster head node looses contact to the NAS for reasons that are unknown to us. The mount command reports that the filesystems are mounted but the df command hangs and it is impossible to cd to the mounted file systems. All other hosts and the cluster nodes continue to see the NAS, so the problem does not seem to lie with the NAS. The head node is running a FreeNX server to allow users graphical sessions.

If we try to unmount the 'stale' file system we get the error message that it is 'busy'. This is also true if we try unmount -f. The only way to get things working again is to reboot the head node.

We would be grateful for any suggestions that can help us next time this happens.
In other words
* What could cause df to hang when we know the NAS server is running?
* How can we troubleshoot the issue next time it happens?

---

### Post by clrg on 2010-09-12
For hints to what went wrong, check the /var/log/* files.

If you want to force-umount an unresponsive filesystem, do a umount -l, it usually works better than -f. You can check for active file handles with the fuser command (but it'll probably hang too, just as df).

Instead of rebooting, simply restart the nfs client service (forgot its name, you should find it in /etc/init.d or /etc/init).

I used an Ubuntu nfs server at home (accessed by multiple Ubuntu clients), and I had stale filesystems every few days. The only thing that helped was to restart the nfs service on the server, reboot the clients and remount all nfs filesystems. I asked for help in several forums, but no one offered a solution. Out of desperation, I moved everything to Samba, and I didn't have any problems ever since. I'm sorry I can't offer a real solution. 

If you are using the Ubuntu cluster professionally, call the Canonical support. I hear they're very good.

---


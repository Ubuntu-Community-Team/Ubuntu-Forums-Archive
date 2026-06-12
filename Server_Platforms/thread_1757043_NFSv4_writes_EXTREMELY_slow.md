---
title: "NFSv4 writes EXTREMELY slow"
date: 2011-05-13
forum: Server Platforms
---

### Post by warensemble on 2011-05-13
I have a 4 disk mdadm raid 5 ubuntu server 10.04 setup and ubuntu 10.10 desktop. I have nfs4 setup on the server and a share mounted on the desktop. Over gigabit I get around 50-60 MBps read from the server but around 2-5 MBps write to the server. With samba I get around 100+MBps to the server. There is something obviously wrong and I'm not sure where to even start troubleshooting this. If you need me to post something, let me know.

EDIT: running nfs-kernel-server

thanks for the help!

---

### Post by SeijiSensei on 2011-05-13
Try adding "async" to the options list in /etc/exports.  Unless you're really worried about the NFS server going down before it's flushed all its buffers, async shouldn't cause problems.

You might also want to increase the rsize and wsize parameters.  I'm using 65536 these days.

You can also add these parameters to the entry in /etc/fstab.

Take a look at "man mount" to see an exhaustive list of NFS parameters.

---

### Post by warensemble on 2011-05-14
So I enabled async and it helped drastically however my reads and writes are still nearly half of those of samba. rsize and wsize adjustments made a little difference, but not much. Every thread on nfs says that it should be faster than samba/cifs, I'm not entirely sure how to get those speeds.
What could be the problem?

thanks!

---

### Post by warensemble on 2011-05-15
bump!

---


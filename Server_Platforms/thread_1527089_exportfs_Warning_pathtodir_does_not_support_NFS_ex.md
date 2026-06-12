---
title: "exportfs: Warning: /path/to/dir does not support NFS export."
date: 2010-07-08
forum: Server Platforms
---

### Post by lfitz on 2010-07-08
hi,

exportfs outputs the following error upon restart or after editing /etc/exports.

```
'exportfs: Warning: /exports does not support NFS export.'
```here is my info and configs.

[http://lfitz.bravehost.com/nfs-error.html](http://lfitz.bravehost.com/nfs-error.html)

-----------------

On second thought, here is the contents of the webpage. 

Start with:  [I]apt-get install nfs-kernel-server

[/I] Ubunut 9.04 (Jaunty) Server
Kernel: 2.6.30.2 #11
Arch: ARMv5 on SheevaPlug
  Error output:  *exportfs -rav*   OR   */etc/init.d/nfs-kernel-server restart*

exporting 10.0.0.100:/exports
exportfs: Warning: /exports does not support NFS export.
  Server Info:  [I]ls -la /exports

[/I] total 12
drwxr-xr-x  5 root  root   352 Jul  7 00:07 .
drwxr-xr-x 21 root  root  1376 Jul  7 13:24 ..
drwxr-xr-x  3 root  root  4096 Jul  7 00:06 ftproot
drwxr-xr-x 12 lfitz lfitz 4096 Jul  8 00:19 lfitz
drwxr-xr-x  2 root  root  4096 Jul  6 20:38 webroot
   [I]cat /etc/exports

[/I] /exports                10.0.0.100(rw,sync,no_subtree_check,nohide,fsid=0)
/exports/lfitz         satellite(rw,sync,no_subtree_check,nohide)
/exports/ftproot       satellite(rw,sync,no_subtree_check,nohide)
/exports/webroot       satellite(rw,sync,no_subtree_check,nohide)
 
  *mount -l*

...snip...

rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
/dev/mmcblk0 on /mnt/storage type ext2 (rw) [sheeva-storage]
/mnt/storage/webroot on /exports/webroot type none (rw,bind)
/mnt/storage/ftproot on /exports/ftproot type none (rw,bind)
/mnt/storage/lfitz on /home/lfitz type none (rw,bind)
/mnt/storage/lfitz on /exports/lfitz type none (rw,bind)
 
  *cat /etc/hosts.allow*

nfsd:   10.0.0.100
portmap: 10.0.0.100
mountd: 10.0.0.100
 
 Client Info:   *cat /etc/fstab*

sheeva:/	/mnt/sheeva			nfs4 	rw 	0	0
sheeva:/lfitz	/mnt/sheeva/lfitz		nfs4	rw	0 	0
sheeva:/ftproot /mnt/sheeva/ftproot		nfs4	rw	0	0
sheeva:/webroot	/mnt/sheeva/webroot		nfs4	rw	0	0
   *mount -a*

mount.nfs4: mounting sheeva:/exports/lfitz failed, reason given by  server:
  No such file or directory
mount.nfs4: mounting sheeva:/exports/ftproot failed, reason given by  server:
  No such file or directory
mount.nfs4: mounting sheeva:/exports/webroot failed, reason given by  server:
  No such file or directory
  Basically, the server will not export the directory */exports*.  Is  there anyway to fix this?

---

### Post by Peppuzzo on 2010-08-19
Same here. Cannot get my NFS to work this way. I am on Lucid Lynx.

---

### Post by arrrghhh on 2010-08-19
Perhaps the bind mount is the issue...?  I'm not sure.  What are you doing that's similar to the OP?

And to the OP, did you ever sort this out?

---

### Post by kellymartinv on 2010-08-24
I was just having the same problem and stumbled upon this post.  I am able to use NFS with several folders, but not on a folder in my home directory.  My guess now is that it's because I have an automatically encrypted home folder... 

When I created another folder outside my home folder (i.e., change /home/user/folder to /home/folder) it worked just fine.

I'm using both ext3 and ext4 for the shares, btw.

---

### Post by Nessined on 2010-11-09
I have a similar problem on a sheevaplug. For me the root cause is that the main nfs4 export directory is situated on an ext4 filesystem. If I move it to an ext3 filesystem all problems are gone. It is fully described in following debian bug report: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=602956](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=602956)

---

### Post by jdepi on 2011-03-03
Although my 10.04.1 LTS server complains the same:
exportfs: Warning: /var/lib/vmware/Virtual Machines does not support NFS export.
   ...done.
 * Starting NFS kernel daemon
   ...done.
It works nonetheless: my 10.10 desktop client connects without any troubles!

(let me note: all these systems run on intel CPUs)

---

### Post by heffae on 2011-05-28
I was having this exact same problem.  In my case I was trying to export a directory that was already mentioned in my autofs configuration (specifically /etc/auto.direct).  This was because I'm migrating files between two servers and I forgot to delete auto mounts from my "New" file server.

Removing the directory from /etc/auto.direct.

---


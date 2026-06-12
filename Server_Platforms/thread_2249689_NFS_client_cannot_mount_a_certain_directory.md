---
title: "NFS client cannot mount a certain directory"
date: 2014-10-24
forum: Server Platforms
---

### Post by Yousan on 2014-10-24
Hello!

I am replacing file server with Ubuntu. The previous file server was made by FreeBSD with ZFS.
I need NFS function at new Ubuntu server. I am trying to export directories but I cannot.
The point is "Some directories can be mounted" but "Other directories cannot be mounted."
Such as
```

nfsserver> cat /etc/fstab
...
/mnt/pool/home      /home               none      bind              0       0  # local use
/mnt/pool/home      /exports/home   none      bind              0       0  # to be exported, correctly
/mnt/pool/share      /exports/share    none      bind              0       0  # to be exported, correctly
/mnt/pool/mail       /exports/mail       none      bind              0       0 # to be exported, correctly
/mnt/pool/hoge      /exports/hoge      none      bind              0       0 # to be exported, incorrect
/mnt/pool/ss          /exports/ss      none      bind              0       0 # to be exported, incorrect
/mnt/pool/ssowncloud      /exports/ssouncoud      none      bind              0       0 # to be exported, incorrect

nfsserver>  ls /mnt/pool/hoge
home  mail   share ss ssowncloud

nfsserver> mount -v
...
/dev/md127 on /mnt/pool type xfs (rw,noatime)
/mnt/pool/home on /home type none (rw,bind)
/mnt/pool/home on /exports/home type none (rw,bind)
/mnt/pool/share on /exports/share type none (rw,bind)
/mnt/pool/ssowncloud on /exports/ssowncloud type none (rw,bind)
/mnt/pool/ss on /exports/ss type none (rw,bind)
nfsd on /proc/fs/nfsd type nfsd (rw)
/mnt/pool/mail on /exports/mail type none (rw,bind)
/mnt/pool/hoge on /exports/hoge type none (rw,bind)

nfsserver> cat /etc/exports
...
/exports       192.0.2.0/24fsid=0,no_subtree_check,no_root_squash,rw)
/exports/home   192.0.2.0/24(async,nohide,no_subtree_check,no_root_squash,rw)
/exports/share  192.0.2.0/24(async,nohide,no_subtree_check,no_root_squash,rw)
/exports/mail   192.0.2.0/24(async,nohide,no_subtree_check,no_root_squash,rw)
/exports/mail2  192.0.2.0/24(async,nohide,no_subtree_check,no_root_squash,rw)
/exports/ssowncloud     192.0.2.0/24(async,nohide,no_subtree_check,no_root_squash,rw)
/exports/ss     192.0.2.0/24(async,nohide,no_subtree_check,no_root_squash,rw)



nfsclient> cat /etc/fstab
...
nfsserver.example.com:/home               /home                    nfs4     rw,noatime  0       0   # correctly
nfsserver.example.com:/mail               /mnt/mail                    nfs4     rw,noatime  0       0   # correctly
nfsserver.example.com:/share               /mnt/share                    nfs4     rw,noatime  0       0   # correctly
nfsserver.example.com:/hoge              /mnt/hoge                    nfs4     rw,noatime  0       0   # incorrectly

nfsclient> sudo mount fs.l2tp.org:/hoge /mnt/hoge
mount.nfs: Connection timed out

nfsclient> sudo mount fs.l2tp.org:/export/hoge /mnt/hoge
mount.nfs: Connection timed out

nfsclient> showmount -e nfsserver.example.com
Export list for bush.l2tp.org:
/exports/ss         192.0.2.0/24
/exports/ssowncloud 192.0.2.0/24
/exports/hoge      192.0.2.0/24
/exports/mail       192.0.2.0/24
/exports/share      192.0.2.0/24
/exports/home       192.0.2.0/24
/exports            192.0.2.0/24

```

home, share and mail directories are mounted correctly. but hoge, ss and ssowncloud cannot be mounted.
When I add a new directory
```

nfsserver> sudo mkdir /mnt/pool/foo
nfsserver> sudo mkdir /exports/foo
# add bind mount line to fstab
nfsserver> sudo mount -a
# add expots line to exports
nfsserver> sudo exportfs -ra; sudo service nfs-kernel-server restart

nfsclient> sudo mkdir /mnt/foo
nfsclient> sudo mount nfsserver.example.com:/foo /mnt/foo
#failed!

```

Any Ideas?

thanks!

```

nfsserver> more /etc/issue
Ubuntu 14.04.1 LTS \n \l
nfsclient> more /etc/issue
Ubuntu 14.04.1 LTS \n \l

```

---

### Post by Yousan on 2014-11-14
Hello.

I could resolve this problem.

Now XFS might have a problem at being used as NFS exports.

[https://www.mmacleod.ca/blog/2014/02/nfs-exports-and-xfss-inode64-mount-option/](https://www.mmacleod.ca/blog/2014/02/nfs-exports-and-xfss-inode64-mount-option/)

I added fsid option like this

nfsserver> cat /etc/exports
...
/exports       192.0.2.0/24(fsid=0,async,wdelay,insecure,no_subtree_check,no_root_squash,rw)
/exports/home  192.0.2.0/24(fsid=1,async,wdelay,insecure,nohide,no_subtree_check,no_root_squash,rw)
/exports/share 192.0.2.0/24(fsid=2,async,wdelay,insecure,nohide,no_subtree_check,no_root_squash,rw)
/exports/mail  192.0.2.0/24(fsid=3,async,wdelay,insecure,nohide,no_subtree_check,no_root_squash,rw)
/exports/mail2       192.0.2.0/24(fsid=4,async,wdelay,insecure,nohide,no_subtree_check,no_root_squash,rw)
/exports/ssowncloud  192.0.2.0/24(fsid=5,async,wdelay,insecure,nohide,no_subtree_check,no_root_squash,rw)
/exports/ss 192.0.2.0/24(fsid=6,async,wdelay,insecure,nohide,no_subtree_check,no_root_squash,rw)

I hope this thread might help someone.

Thanks.

---


---
title: "LDAP user permissions work but group permissions don't"
date: 2012-05-10
forum: Server Platforms
---

### Post by duffrecords on 2012-05-10
I have a server that can successfully authenticate logins via an LDAP server.  If a directory on the server is owned by an LDAP user, that user can write to it.  However, the same does not hold true for group permissions.  For example, the following directory is not writable by the user iyoung::```
iyoung@samba:~$ ls -l /mnt/gluster
drwxrwxr-x  3 root  TechOps                   70 2012-04-09 14:27 techops
```even though the user is a member of the TechOps LDAP group:```
iyoung@samba:~$ getent group | grep TechOps
TechOps:*:10001:iyoung
```And yes, /etc/nsswitch.conf is set as follows:```
group:          ldap files
```Why can't I write to this directory?
```
iyoung@samba:~$ touch /mnt/gluster/techops/test
touch: cannot touch `/mnt/gluster/techops/test': Permission denied
```

---

### Post by duffrecords on 2012-05-11
I found that this only happens on NFS-mounted Gluster volumes.  As long as the directory is owned by my primary group I can write to it.  Secondary groups are apparently not considered.  So now I have a directory that a group of developers can write to (assuming everybody has the same primary gid in LDAP) but that means I can't regulate access to different directories based on group membership (i.e. folder 1 is writable by one group, folder 2 writable by another, folder 3 writable by both groups).

:(

---


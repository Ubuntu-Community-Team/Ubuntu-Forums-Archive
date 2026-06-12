---
title: "nfs hides directories"
date: 2007-03-07
forum: Server Platforms
---

### Post by ianare on 2007-03-07
using 7.04

```
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#

/mnt/storage    192.168.1.0/255.255.255.0(rw,sync,no_root_squash,subtree_check,nohide)
```

When I mount this share on another system, it only mounts the toplevel directories, but not any of the sub directories or files.

Any suggestions?

---

### Post by Mr. C. on 2007-03-07
man exports

       nohide 
...
              The nohide option is currently only effective on single host exports.  It does not work reliably with netgroup, subnet, or wildcard exports.

---

### Post by ianare on 2007-03-08
i tried it with the nohide option as well, same problem

---

### Post by ianare on 2007-03-08
i tried it without the nohide option as well, same problem

---

### Post by Mr. C. on 2007-03-08
You need nohide to share mounted subdirs.  Now with that, re-read the disclaimer I quoted for you from man exports.

MrC

---


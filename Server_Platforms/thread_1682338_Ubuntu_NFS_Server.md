---
title: "Ubuntu NFS Server"
date: 2011-02-05
forum: Server Platforms
---

### Post by fellixombc on 2011-02-05
when I do: ```
sudo mount 190.168.1.3:/home/sam/public_html/ /var/www/
```

it returns to me: ```
mount.nfs: access denied by server while mounting 190.168.1.3:/home/sam/public_html/

```

my /etc/exports:
```

# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_sub$
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#

/home/sam/public_html 192.168.1.0/24(rw,sync,no_subtree_check)

```

```
/etc/hosts.allow
ALL:190.168.1.0/24
/etc/hosts.deny
portmap ALL
lockd: ALL
mountd: ALL
rquotad: ALL
statd: ALL
```

Fixed, just messed around a bit with the  190.168.1.0/24 thing

sorry for posting a useless thread

---


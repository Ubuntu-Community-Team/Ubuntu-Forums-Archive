---
title: "SAMBA 3.6.6 acl problem"
date: 2013-01-22
forum: Server Platforms
---

### Post by zvoice on 2013-01-22
Part of samba 3.6.6 conf
```

[global]
...
workgroup = WORKGROUP
server string = Samba Server %v
security = user
guest ok = no
map to guest = never

inherit permissions = Yes
inherit acls = Yes

map acl inherit = Yes
map archive = no
map hidden = no
map read only = no
nt acl support = yes
acl compatibility = auto
store dos attributes = yes

[share1]
...
inherit owner = Yes
vfs objects = acl_xattr

```

```
$ getfacl share1/
# file: share1/
# owner: user
# group: sambagroup
# flags: -s-
user::rwx
group::r-x
group:sambagroup:r-x
group:control:rwx
mask::rwx
other::---

$ id user 
uid=1004(user) gid=1002(sambagroup) groups=1002(sambagroup),1015(control)
```

and when I 
```

su - user
cd share1/
touch testfile

```
it succeeds, but when I do that from samba (from  windows machine) - it fails.

What's wrong with my configs?

---

### Post by wyliecoyoteuk on 2013-01-22
Samba and Unix permissions don't always map well.
I would say that the Unix file creation defaults are set to a different default user.

this link might explain it better:

[http://lists.samba.org/archive/samba/2011-August/163958.html](http://lists.samba.org/archive/samba/2011-August/163958.html)

---


---
title: "samba and owning user not in owning group"
date: 2012-01-23
forum: Security
---

### Post by floobit on 2012-01-23
I want some power users to have read access to everyone's home directories.  They should not have any command-line access, however, let alone sudo.  I thought I could solve this by making them members of a poweruser group (powergrp), then chowning all homedirs to powergrp and chmodding them 770.  Each user would be able to access their homedir normally, and the powerusers would be able to as well through the group ownership.  In normal linux, I get the expected behavior.  Samba chokes, however, disallowing any access to a homedir permissioned as such.  Is there a way to enable samba to correctly parse permissions with an owning user that does not belong to the owning group?

Will I have to resort to ACLs?

---

### Post by emiller12345 on 2012-01-25
have you configured your smb.conf file to include a share with an entry that contains 
```
read only = yes

```
take a look here
[http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html](http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html)

---


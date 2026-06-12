---
title: "ACL not operating as expected"
date: 2012-04-07
forum: Security
---

### Post by thomasgrzybowski on 2012-04-07
Hi, I don't understand why my ACL entry is not working as I expect.

Here is the command that I use to set the acl:

setfacl -m u:tg:rwx  .profile

Here is the result of getfacl:
getfacl .profile
# file: .profile
# owner: tg
# group: tg
user::rw-
user:tg:rwx
group::rw-
mask::rwx
other::---

Why can't I (owner tg) execute .profile?

---


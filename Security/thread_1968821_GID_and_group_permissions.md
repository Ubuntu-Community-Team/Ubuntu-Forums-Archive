---
title: "GID and group permissions"
date: 2012-04-29
forum: Security
---

### Post by dstahl80 on 2012-04-29
Ubuntu 10.04
I am trying to understand *exactly* how permissions work:

foo is text file with these permissions:
- --- r-- --- bar baz [yadda yadda] foo
foo is owned by bar, group owned by baz
i.e, has only read permission for the group.

user bar whose primary group is baz, which has group read permission on foo, does this:
cat foo
... resulting in
cat: foo: Permission denied

Can someone please explain this to me?

---

### Post by JKyleOKC on 2012-04-29
It's actually quite simple. The permissions for the owner override the other permission fields, and you've defined them in such a way as to deny bar, the owner, all access to the file. However, all other members of the group would be able to read it. To allow bar the same ability, you would need to set the permissions to r--r----- so that the owner has read access.

---


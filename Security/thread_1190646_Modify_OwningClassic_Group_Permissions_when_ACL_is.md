---
title: "Modify Owning/Classic Group Permissions when ACL is Active"
date: 2009-06-18
forum: Security
---

### Post by Lucky. on 2009-06-18
Hi everyone,

I am trying to understand POSIX ACLs some more.  Since the ACL mask sits in place of the classic/owning group permissions, the chmod command no longer modifies the permissions of the owning group...it modifies the permissions of the ACL mask.

An example (with a username of "lucky")
```

umask 027
mkdir stuff

```

ls -l shows the following:

```

drwxr-x--- lucky lucky (blah blah blah)

```

Then after applying an ACL entry...

```

setfacl -m user:somedude:rwx stuff

```

ls -l shows the following:

```

drwxrwx---+ lucky lucky (blah blah blah)

```

getfacl stuff shows something like:

```

user::rwx
user:somedude:rwx
group::r-x
mask::rwx
other::---

```

One might think that chmod 700 would change the owning group permissions, but instead it modifies the ACL mask:

```

user::rwx
user:somedude:rwx    effective:---
group::r-x           effective:---
mask::---
other::---

```

That's understandable, but now I'm trying to figure out how to change the permissions on the owning group itself.  It doesn't appear as if I can use chmod anymore (perhaps I am wrong).  I honestly can't find a reason to even mess with the owning group anymore once ACLs are in place, but I'd still like to know how to do it just in case.

Anybody know how to modify classic group permissions after an ACL mask is in place?

---

### Post by Lucky. on 2009-06-19
Never mind, the answer is obvious.

```

setfacl -m group::r-- stuff

```

This changes the owning/classic group permissions.

I figured that I would always be using setfacl for the extended portion, and chmod for classic stuff.  Guess not.  setfacl is a suitable replacement of chmod for both classic and extended permissions once an ACL is applied.

---


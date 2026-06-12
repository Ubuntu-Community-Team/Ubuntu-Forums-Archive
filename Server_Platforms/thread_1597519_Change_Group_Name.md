---
title: "Change Group Name"
date: 2010-10-15
forum: Server Platforms
---

### Post by gfariello on 2010-10-15
I just changed a group name from foo to foolocalgrp:

```
% cat /etc/group | egrep '^foo'
foo:x:1000:
% groupmod --new-name foolocalgrp foo
% cat /etc/group | egrep '^foo'
foolocalgrp:x:1000:
```

All is good, or so it seems. Now I try to add a new group (with a new id) with the name "foo", and it's a no-go:

```
% groupadd foo --gid 5004
groupadd: group 'foo' already exists
% groupmod foo --gid 5004
groupmod: group 'foo' does not exist in /etc/group
```

So, group "foo" already exists, but it doesn't exist. Anyone have any ideas?

Thanks!

---

### Post by luvshines on 2010-10-15
Can you check if GID 5004 already exists in /etc/group ?

---

### Post by gfariello on 2010-10-15
It seems that there was a network Kerberos group conflict.

---


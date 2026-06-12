---
title: "Samba share and &quot;valid users&quot;"
date: 2008-12-23
forum: Server Platforms
---

### Post by pongtawat on 2008-12-23
Hello all,

I have a problem migrating my samba config from Dapper to Hardy. On Dapper, I have a share with 

valid users = @users

which work fine. 

On Hardy, that share config doesn't work ("connect failed: NT_STATUS_ACCESS_DENIED").

However, if I change from "@users" to list of user, e.g. 

valid users = joe jane

it work.

More strangely, if I add a new group to my system (say "sharetest"), add user to that group and change valid users to:

valid users = @sharetest

it also work.

It seem like only @users has problem.

Does anybody know how to fix this?

Thank you in advance,
Pongtawat

PS. I have searched the forum and found someone else having the same problem. But unfortunately, there is no solution given.

---

### Post by thomas_d_j on 2012-08-18
Sorry old post but just had same problem.

The issue turned out to be that my users were not actually members of the "users" group:
```
me:~$ groups foo
foo

```

solution was simple:
```
me:~$ sudo usermod -G users -a foo
me:~$ groups foo
foo users
```

---


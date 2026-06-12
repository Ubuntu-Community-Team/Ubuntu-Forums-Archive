---
title: "xauth error in locking authority file"
date: 2012-03-12
forum: Server Platforms
---

### Post by Oakenshields on 2012-03-12
Hello,
this "locking" issue has been discussed dozens of times, however none of what I've found solved my problems with two servers (all running 11.10 Server).

Short version:
- Three Servers A, B, C.
- Roles of A
  - NIS Server for passwd, shadow and group
  - NFS Server for homes
  - LDAP-Client to authenticate Users with a university account (other department)
  - Some local users in passwd & shadow for local accouns without univ account
- Roles of B and C
  - mount homes via NFS (so .Xauthority is on mounted NFS home)
  - LDAP-Client to authenticate Users with a university account (as on A)
  - NIS Client to also authenticate local users  via A
- A and B are in the same building and network segment
- C is in another building and another segment

Problem:
- as normal user being logged in on C via putty (no X involved) executing xauth list throws: xauth:  error in locking authority file...
- consequently the same error occurs if I try to login with ssh -C -Y
- as root everything is fine.
- on B everything is fine for both root and normal user.

Permissions on the .Xauthority are 600 to the user. Via putty on C, when the xauth fails as normal user, the user can nonetheless read the file and touch it. So he should be able to lock it. Iam running out of ideas what more to test. Could anyone give me a hint what to try?
Best,

Peter

---

### Post by Oakenshields on 2012-03-19
In answer to myself, and maybe other who observed this behaviour :-).
Of course it had to do something which access to the .Xauthority, but not that trivial
It turned out, that the NFS settings were still from NFS3 times and miricually worked for some time. A proper configuration of exports and import settings on solved the problem.

---


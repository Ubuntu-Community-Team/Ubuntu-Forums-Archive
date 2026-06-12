---
title: "LDAP and &quot;bdb_equality_candidates: not indexed&quot;"
date: 2009-06-25
forum: Server Platforms
---

### Post by JeppeM on 2009-06-25
Hey all,

I have been trying to find the solution for this problem for quite some time, but I don't think I know enough about LDAP to figure it out. My problem is that I have a server using ebox with the users and groups module. I get a lot of these errors in the log:

```
Jun 25 11:19:12 fileserver slapd[11493]: <= bdb_equality_candidates: (gidNumber) not indexed 
Jun 25 11:19:12 fileserver slapd[11493]: <= bdb_equality_candidates: (sambaGroupType) not indexed 
Jun 25 11:19:12 fileserver slapd[11493]: <= bdb_equality_candidates: (sambaSIDList) not indexed 
Jun 25 11:19:12 fileserver slapd[11493]: <= bdb_equality_candidates: (sambaGroupType) not indexed 
Jun 25 11:19:12 fileserver slapd[11493]: <= bdb_equality_candidates: (sambaSIDList) not indexed 
Jun 25 11:19:24 fileserver slapd[11493]: <= bdb_equality_candidates: (uid) not indexed 
Jun 25 11:19:24 fileserver slapd[11493]: <= bdb_equality_candidates: (uid) not indexed 
Jun 25 11:19:24 fileserver slapd[11493]: <= bdb_equality_candidates: (memberUid) not indexed
```

Now, I know that the error is related to some indexation in LDAP not being right, and I think I should run slapindex, but I'm not sure how exactly to do it, since I get some errors related to permissions if I just run slapindex as root / with sudo.

Can anyone help with this? I would think that it's a minor issue and easy to fix, but I'm not 100% sure exactly how to do it :)

---

### Post by ghen on 2009-06-25
First stop slapd then run slapindex. It should be fine.

If you get:
# Correct the ownership of the index files ..

then do as requested:
```
sudo chown openldap:openldap /var/lib/ldap/*
```

and start slapd again.

---

### Post by lisanels47 on 2012-05-18
I have this index issue also.

(memberUid) not indexed
(member) not indexed
(uidNumber) not indexed

root@hs78-01:/var/lib# slapindex

WARNING!
Runnig as root!
There's a fair chance slapd will fail to start.
Check file permissions!

Looks like this didn't work, but slapd did start like usual...

---

### Post by slau on 2012-08-03
Subscribe , same problem ... 

WARNING!
Runnig as root!
There's a fair chance slapd will fail to start.
Check file permissions!


4 drwxr-x---  2 openldap              openldap              4096 2012-08-03 15:35 ldap


And still have some problem.....

---


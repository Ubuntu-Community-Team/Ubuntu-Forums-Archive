---
title: "Users with login capabilities"
date: 2012-02-10
forum: Security
---

### Post by matthewboh on 2012-02-10
I'm trying to make sure that all accounts that are NOT associated with a person change their logins every 90 days.

Accounts associated with people are being forced to change their passwords through LDAP, so I'm not worried about them.

Accounts that can not login - not worried about those either.

Do I just look for the entries in /etc/passwd with a User ID greater than 1000?

Thanks!

---

### Post by emiller12345 on 2012-02-11
to list the status of all accounts on the computer 
```
# passwd -a -S
null-user L 02/11/2012 0 99999 7 -1
user P 02/11/2012 0 99999 7 -1

```
the second column tells if it has a locked password (L), has no password (NP), or has a usable password (P)
for info on how passwd works
```
$ man passwd
```
under the -S area

---


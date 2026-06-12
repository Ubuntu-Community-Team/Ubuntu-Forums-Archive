---
title: "ldap offline login"
date: 2011-07-25
forum: Server Platforms
---

### Post by le_fada on 2011-07-25
Hi all ! :D

I'm trying to design a linux workstation with a network authentication. The authentication is based on LDAP+SSL.
The authentication works well as long as the station is plugged on the network. To permit offline login, I tried to set up libnss-db, nss-updatedb and libpam-ccreds.

My problem comes from nss-updatedb, which is not able to dump the ldap info from the server. Error is "Failed to enumerate nameservice: No such file or directory"

Browsing the forum and the internet, i red that the typical mistake is to misconfiguring the uri in ldap.conf/nslcd.conf.

To be sure, I tried to follow the system calls :```
strace -o /tmp/strace_nss nss_updatedb ldap
```I can see the users infos being dumped from the ldap, and from nowhere, this error...#-o

Finally, i downloaded the latest source code of nss_updatedb and try to compile it : i got a warning with mktemp :
```
cache.c:73: warning: the use of `mktemp' is dangerous, better use `mkstemp' or `mkdtemp'
```The error "No such file or directory" comes from the temp file not created (because it is dangerous...), and so no local cache, and no offline login...

Any idea to solve this issue ?!](*,)

Kind regards,
Laurent.

EDIT: I'm surprised that nss_updatedb is not up-to-date. I'm not at ease with C programming, but if I can fix this, that can be a solution...
Or is exiting another tool that doing cache with pam/nss and network login ?!

---

### Post by le_fada on 2011-07-29
Hi all, here is the solution.

No problem with mktemp. mktemp does not create the temporary file as mkstemp do, it just create the unique name. This is the way mktemp work, so no problem with nss_updatedb.


The problem came from the fact that nslcd ask all the users/groups in the ldap in 1 time. In the LDAP I use, there are many entries, so the size of the response is too huge. To make it work easily, just tell to nslcd to make shorter responses:

```
echo "pagesize 500" >> /etc/nslcd.conf
```And this is it.

---


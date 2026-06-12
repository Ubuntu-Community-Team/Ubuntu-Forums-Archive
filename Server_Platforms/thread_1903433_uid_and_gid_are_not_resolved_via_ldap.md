---
title: "uid and gid are not resolved via ldap"
date: 2012-01-02
forum: Server Platforms
---

### Post by johanneskoester on 2012-01-02
Hello there,
I configured an LDAP server with default settings on an Ubuntu 11.10 server machine.

While User creation and login works fine, I have one issue when logging in with an LDAP user:

If I log in on a client:
ls -l somefile
on a file mounted via nfs shows the following instead of user and group
-rw-rw-r-- 1 4294967294 4294967294 0 2012-01-02 16:36
Apart from that, I have no problems in creating and reading these files, however chown does not work.

If I do the same on the server on which the LDAP server runs and where the directory is not mounted via NFS, everything works ok:
-rw-rw-r-- 1 test test 0 2012-01-02 16:36

The server and the clients have exactly the same /etc/pam.d/common-* files, and /etc/ldap.conf.

Does anybody have a hint what causes the problems when accesing the files via NFS?

Thanks in advance for your help. Let me know if you need any additional information.
Johannes

---

### Post by rsvancara on 2012-01-02
How are your exports configured on the server?  That is a pretty high UID and GID for file permissions.

---

### Post by johanneskoester on 2012-01-03
Yes they are:
/vol/home       10.90.129.0/21(rw,async,no_subtree_check)

You are right the uid and gid is very high. Especially, it is not the real uid and gid that was set on the server (2001:2003).

---

### Post by johanneskoester on 2012-01-03
I solved it myself:
Since I use NFSv4 I had to activate idmapd and add the option 
```
[Translation]

Method = nsswitch
```

Further, NFS4 requires the exports to reside in /export via a bind mount in order to work properly with idmapd.

Thank you for your help.
Johannes

---

### Post by rsvancara on 2012-01-03
Awesome find.  I have not used NFS V4 yet, so this is something that is good to know.  Thanks for taking the time to figure this out!

---

### Post by rsvancara on 2012-01-03
Awesome find.  I have not used NFS V4 yet, so this is something that is good to know.  Thanks for taking the time to figure this out!

---


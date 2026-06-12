---
title: "MySQL server and SSL certificate error"
date: 2008-12-17
forum: Server Platforms
---

### Post by mikey_p on 2008-12-17
I'm trying to setup MySQL to use (and eventually require) SSL for some users. I've got through all the setup steps and generated client and server certificates, but I'm getting a small note in the syslog about not being able to get the SSL cert:

```
Dec 17 20:34:46 martin mysqld[31277]: SSL error: Unable to get certificate from '/etc/mysql/ssl/server-cert.pem'
Dec 17 20:34:46 martin mysqld[31277]: 081217 20:34:46 [Warning] Failed to setup SSL

```

Followed by these two related lines:

```
Dec 17 20:43:06 martin kernel: [4142597.491683] audit(1229568186.157:22): type=1503 operation="inode_permission" requested_mask="r::" denied_mask="r::" name="/etc/mysql/ssl/cacert.pem" pid=31490 profile="/usr/sbin/mysqld" namespace="default"
Dec 17 20:43:06 martin kernel: [4142597.491702] audit(1229568186.157:23): type=1503 operation="inode_permission" requested_mask="r::" denied_mask="r::" name="/etc/mysql/ssl/server-cert.pem" pid=31490 profile="/usr/sbin/mysqld" namespace="default"
```

Any idea why this would be?  Is there a way to verify/test the certificate to make sure it's valid?

---


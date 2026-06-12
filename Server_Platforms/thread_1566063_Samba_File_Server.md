---
title: "Samba File Server?"
date: 2010-09-01
forum: Server Platforms
---

### Post by TheCraneMan on 2010-09-01
Alright so I have been following the Woodel.com HOWTO on building a server, and I've seemed to manage up until this. I have gotten to the Samba section, but when I install the "samba4" and "samba" packages I get the following errors from the samba4 daemon

```

root@computer:/etc/init.d# samba start
Unknown parameter encountered: "sync always"
Ignoring unknown parameter "sync always"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "allow hosts"
Ignoring unknown parameter "allow hosts"
Unknown parameter encountered: "wide links"
Ignoring unknown parameter "wide links"
Unknown parameter encountered: "delete readonly"
Ignoring unknown parameter "delete readonly"
Unknown parameter encountered: "writeable"
Ignoring unknown parameter "writeable"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "os level"
Ignoring unknown parameter "os level"
Unknown parameter encountered: "create mode"
Ignoring unknown parameter "create mode"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "directory mode"
Ignoring unknown parameter "directory mode"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"

``` 

I have been configuring Samba via the Webmin module, could this be a problem? Thank's in advance! --Canute

---

### Post by TheCraneMan on 2010-09-01
Also when I try to Restart it from the Webmin interface, it gives me the error:

```
**Failed to restart Samba servers : /etc/init.d/samba start  failed**


```

---

### Post by redmk2 on 2010-09-01
> **TheCraneMan said:**
> Alright so I have been following the Woodel.com HOWTO on building a server, and I've seemed to manage up until this. I have gotten to the Samba section, but when I install the "samba4" and "samba" packages I get the following errors from the samba4 daemon

```

root@computer:/etc/init.d# samba start
Unknown parameter encountered: "sync always"
Ignoring unknown parameter "sync always"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "allow hosts"
Ignoring unknown parameter "allow hosts"
Unknown parameter encountered: "wide links"
Ignoring unknown parameter "wide links"
Unknown parameter encountered: "delete readonly"
Ignoring unknown parameter "delete readonly"
Unknown parameter encountered: "writeable"
Ignoring unknown parameter "writeable"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "os level"
Ignoring unknown parameter "os level"
Unknown parameter encountered: "create mode"
Ignoring unknown parameter "create mode"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "directory mode"
Ignoring unknown parameter "directory mode"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"

``` 

I have been configuring Samba via the Webmin module, could this be a problem? Thank's in advance! --Canute

First: Samba4 is experimental.  I would use Samba3 for mainstream use.  

Second: Webmin isn't in the Ubuntu repositories for a good reason: It sometimes is incompatible.  For example, Webmin does not know that 10.04 now uses Upstart.  

This means the restart routines for **smbd **and **nmbd **are different.  That leads to the question in you second post.  To restart Samba (smbd and nmbd) you should [**_follow this post_**]("http://ubuntuforums.org/showthread.php?t=1468111") (note the reference to Webmin).

---

### Post by kevinthecomputerguy on 2010-09-03
The guide at woodel.com has you use Samba 3, how did you arrive at Samba 4?

---

### Post by CharlesA on 2010-09-03
You need to change the way webmin restarts smbd and nmbd in the "module configuration" for Samba in webmin.

But yeah, the guide at woodel.com uses SMB3.x not 4.

---

### Post by kevinthecomputerguy on 2010-09-04
Restarting your server is also an option until this is fixed, if your in a posistion to do so. Restarting your server will do what your after in the above step(s), as a temp fix.

---


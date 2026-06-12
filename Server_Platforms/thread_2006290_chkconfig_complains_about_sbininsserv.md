---
title: "chkconfig complains about /sbin/insserv"
date: 2012-06-18
forum: Server Platforms
---

### Post by SeijiSensei on 2012-06-18
Just came across [this useful solution]("http://loginroot.com/ubuntu-12-04-64bit-sbininsserv-no-such-file-or-directory/") to a bug with chkconfig.   Thought I'd share it with you.

I was trying to disable the openvpn service on a 12.04 server using chkconfig and encountered this error:
 
```
# chkconfig -s openvpn off
/sbin/insserv: No such file or directory
```

The actual file is /usr/lib/insserv/insserv so you need to create a symlink to it like this:

```
cd /sbin
ln -s ../usr/lib/insserv/insserv
```

---

### Post by GAAviator on 2013-01-28
> **SeijiSensei said:**
> Just came across [this useful solution]("http://loginroot.com/ubuntu-12-04-64bit-sbininsserv-no-such-file-or-directory/") to a bug with chkconfig.   Thought I'd share it with you.

I was trying to disable the openvpn service on a 12.04 server using chkconfig and encountered this error:
 
```
# chkconfig -s openvpn off
/sbin/insserv: No such file or directory
```The actual file is /usr/lib/insserv/insserv so you need to create a symlink to it like this:

```
cd /sbin
ln -s ../usr/lib/insserv/insserv
```

I can confirm this bug.  I came up with the same solution and now it works perfectly.

---


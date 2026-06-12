---
title: "Set max ftp connects?"
date: 2010-10-25
forum: Server Platforms
---

### Post by SkyHook15 on 2010-10-25
We have a Ubuntu server with Samba running and pure-ftpd, my father said that ftp has a max of 50 connects on pretty much any Linux box, and he wanted it to be limited to 2 max connects.

I can't figure or find out how to do this, does somebody know a way to set the max ( global not per IP ) ftp connects to a Ubuntu Server?

I've google'd it but can only find per IP settings.

---

### Post by Flybro on 2010-11-17
Hi SkyHook15,

Perhaps you looking for MaxClientsNumber.

```

cd /etc/pure-ftpd/conf/
echo 2 > MaxClientsNumber
/etc/init.d/pure-ftpd restart

```

All details are in:
```
man pure-ftpd-wrapper
```

Cheers,
F.

---


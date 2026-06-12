---
title: "Domain users home directories not being created on Server 18.04"
date: 2019-11-25
forum: Server Platforms
---

### Post by morningstar.fallen on 2019-11-25
I have a domain joined instance of Ubuntu Server 18.04.

I can log in with my AD "administrator account" but I get the below when logging in via console:

```
No directory, logging in with HOME=/
```

And when logging in via ssh I get this:

```
 Could not chdir to home directory /home/AD.MYDOMAIN.COM/administrator: No such file or directory
```

I tried creating the "/home/AD.MYDOMAIN.COM/administrator" manually but when I try

```
sudo chown -R administrator:administrator /home/AD.MYDOMAIN.COM/administrator
```

I get

```
chown: invalid group: ‘administrator:administrator’
```

Any thoughts?

---

### Post by morningstar.fallen on 2019-11-25
Actually, it super easy to fix.

All I had to do was adding the line below to */etc/pam.d/common-session* directly after *session required pam_unix.so*:

```
session    required    pam_mkhomedir.so skel=/etc/skel/ umask=0022 
```

All described here:

[https://help.ubuntu.com/lts/serverguide/sssd-ad.html](https://help.ubuntu.com/lts/serverguide/sssd-ad.html)

---


---
title: "update failure"
date: 2008-11-25
forum: Security
---

### Post by rosswell59 on 2008-11-25
I tried update and got the following error:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gnutls13/libgnutls13_1.6.3-1ubuntu0.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gnutls13/libgnutls13_1.6.3-1ubuntu0.2_i386.deb)
  Could not resolve 'security.ubuntu.com'


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_2.0.0.18+nobinonly-0ubuntu0.7.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_2.0.0.18+nobinonly-0ubuntu0.7.10.1_i386.deb)
  Could not resolve 'security.ubuntu.com'


Why would this happen? Is the problem on my end or on the server?

---

### Post by cdenley on 2008-11-26
> **rosswell59 said:**
> I tried update and got the following error:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gnutls13/libgnutls13_1.6.3-1ubuntu0.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gnutls13/libgnutls13_1.6.3-1ubuntu0.2_i386.deb)
  Could not resolve 'security.ubuntu.com'


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_2.0.0.18+nobinonly-0ubuntu0.7.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_2.0.0.18+nobinonly-0ubuntu0.7.10.1_i386.deb)
  Could not resolve 'security.ubuntu.com'


Why would this happen? Is the problem on my end or on the server?

If you're still having problems, then it's probably on your end. Try posting some more information.
```

nc -z -v 91.189.88.37 80
cat /etc/resolv.conf
dig security.ubuntu.com

```

---


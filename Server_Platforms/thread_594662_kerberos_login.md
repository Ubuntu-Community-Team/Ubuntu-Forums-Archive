---
title: "kerberos login"
date: 2007-10-28
forum: Server Platforms
---

### Post by OldSchool on 2007-10-28
Rather than manually doing ```
kinit; aklog
``` what do I do?

---

### Post by bswilson on 2007-10-31
What exactly are you trying to accomplish?

---

### Post by jbardin on 2007-11-01
here's the changes I use for kerberos authentication (not including a properly configures /etc/krb5.conf)

/etc/pam.d/common-account:
This lets you unset the local password. Personally I like to have a local password in case the kdc or network is down.
```
account required    pam_unix.so broken_shadow
```



/etc/pam.d/common-auth:
This lets either pam_unix or pam_krb5 succeed. Don't forget pam_deny here! without it you can enter the wrong password twice and get logged in.
```
auth    sufficient  pam_unix.so nullok_secure
auth    sufficient  pam_krb5.so ignore_root use_first_pass
auth    required   pam_deny.so
```



/etc/pam.d/common-session:
```
session required    pam_unix.so
session optional    pam_krb5.so
session optional    pam_foreground.so
```

/etc/pam.d/common-password:
```
password   required   pam_unix.so nullok obscure min=4 max=8 md5
password        optional        pam_krb5.so ignore_root
```

---


---
title: "Enabling account lockout in ubuntu using pam_tally"
date: 2011-08-31
forum: Security
---

### Post by nitins on 2011-08-31
I am trying to implement account lockout in ubuntu using pam_tally. I have tried adding the follwing lines in ** /etc/pam.d/common-auth**

   ```
 auth required pam_tally.so deny=3
    account     required  pam_tally.so
```

The failures are getting logged but account is not getting locked even on reaching max failures. I am trying this by directly loggging in (GNOME login screen).

Any advices ? Do I need to add in pam.d/gdm or login file also ?

---

### Post by bodhi.zazen on 2011-09-01
See if this post helps :

[http://blog.bodhizazen.net/linux/ubuntu-how-to-faillog/](http://blog.bodhizazen.net/linux/ubuntu-how-to-faillog/)

---

### Post by nitins on 2011-09-02
> **bodhi.zazen said:**
> See if this post helps :

[http://blog.bodhizazen.net/linux/ubuntu-how-to-faillog/](http://blog.bodhizazen.net/linux/ubuntu-how-to-faillog/)

Tried it. Its getting logged in faillog, but still lockout not happening.

10 failures, still not locked out. :(

---

### Post by bodhi.zazen on 2011-09-02
post your configuration files, the order of the rules counts ;)

---

### Post by nitins on 2011-09-03
Here is my common-auth file.


**grep -v "^#" common-auth **

```
auth required pam_tally.so per_user magic_root onerr=fail
account     required  pam_tally.so


auth    [success=2 default=ignore]    pam_unix.so nullok_secure
auth    [success=1 default=ignore]    pam_winbind.so krb5_auth krb5_ccache_type=FILE cached_login try_first_pass
auth    requisite            pam_deny.so
auth    required            pam_permit.so

```

---


---
title: "PAM broken - passwd does not work"
date: 2009-03-01
forum: Security
---

### Post by L0nk on 2009-03-01
Hi,

I recently upgraded my Ubuntu server to Intrepid. Since the point of upgrade the passwd application cannot change user passwords anymore.

This is what happens:

```
root@man-ma:~# passwd link
New Password:
Reenter New Password:
crypt_r: Don't know 0
Error: Password NOT changed.
passwd: Authentication token manipulation error
passwd: password unchanged
root@man-ma:~#
```

It seems like it accidently uses crypto code 0 to change the password instead of 21 (blowfish). Because yes: everything inside the server has been changed from MD5 to blowfish - mainly because we were migrating from OpenSuse to Ubuntu and users could use there passwords again.

However, until the update to intrepid everything worked. The /etc/pam.d configurations are as followed:

common-password:
```
password required      pam_unix2.so nullok use_authok obscure min=9 max=72 blowfish
```

common-auth:
```
auth    required        pam_unix2.so nullok_secure
```

common-account:
```
account required        pam_unix2.so broken_shadow
```

common-session:
```
session required        pam_unix2.so
session optional        pam_foreground.so
```

Logging in works fine, it's just users cannot switch passwords. Even when I try changing to md5 for tests in common-password I still get the crypt_r error.

Maybe: which apt-get commands would I have to do to completely reinstall PAM and related libraries and reset them to base settings. I would manually switch to blowfish then again.

Thank you,

L0nk

---

### Post by fraterm on 2009-06-09
Assuming no one has helped out with this?  I recently ran into a similar problem with Jaunty here at home.

Existing pre-upgrade users work fine, password manipulation seems to work, but adding a user and setting the password do not seem to work properly.

Every time I run sudo passwd I get token manipulation error messages and the password remains unchanged.

Frustrating as hell, and ubuntu docs assume everything works and don't describe *any* low level detail on the password/pam scheme chosen.

---


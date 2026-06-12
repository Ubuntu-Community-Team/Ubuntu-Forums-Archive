---
title: "ldap and pam: auth sufficient a no-no"
date: 2006-06-13
forum: Server Platforms
---

### Post by thk on 2006-06-13
I just went through setting up pam for ldap client authentication and thought I'd pass along what I found. The instructions on the wiki work for the most part, but can defeat access controls in pam. The wiki docs suggest, eg.
```
auth sufficient pam_ldap.so
auth required pam_unix.so
```
in common-auth, but notice that once you have a sufficient declaration, it overrides any other required directives. If other files include common-auth, their required statements are overridden for ldap users. The solution is in libpam-ldap docs. You can test for users in shadow and skip ldap like this
```
auth [success=1 default=ignore] pam_unix.so nullok_secure
auth required pam_ldap.so use_first_pass
auth required pam_permit.so
```
If the user is not in ldap (eg root), flow jumps directly to pam_permit, otherwise the result of pam_unix is ignored and ldap is tried. Here are the important bits from the other common-* files in /etc/pam.d:
```
account [success=1 default=ignore] pam_unix.so
account required pam_ldap.so
account required pam_permit.so
```
```
session [success=1 default=ignore] pam_unix.so
session required pam_ldap.so
session required pam_permit.so
```
```
password   required   pam_cracklib.so retry=3 minlen=8 difok=3
password   [success=1 default=ignore] pam_unix.so use_authtok md5
password   required   pam_ldap.so use_authtok
password   required   pam_permit.so
```
This was the only way I could get cracklib to work with ldap.

---

### Post by LordHunter317 on 2006-06-13
[QUOTE=thk]The instructions on the wiki work for the most part, but can defeat access controls in pam. The wiki docs suggest, eg.
```
auth sufficient pam_ldap.so
auth required pam_unix.so
```
in common-auth, but notice that once you have a sufficient declaration, it overrides any other required directives.[/quote]No, it does not.  Sufficent works as follows: If and only if no required modules before it have failed and the sufficent module succeeds, then the authentication process is ended.  Otherwise, the authentication process fails after all the other modules proceed.

---

### Post by thk on 2006-06-14
Yes, I should have been more clear -- if you include (eg) common-auth with a sufficient statement, any required's after that inclusion will not be evaluated if the sufficient statement returns success. The Wiki docs are a bit skimpy on that point.

From the README.Debian file:
```
libpam-ldap for Debian
----------------------

- Be very careful when you use "sufficient pam_ldap.so" in Debian's
/etc/pam.d/common-* files: Some services can place other "required"
PAM-modules after the includes, which will be ignored if pam_ldap.so
succeeds. As a workaround, use something like the following construct:
        # Check local authentication first, so root can still login
        # while LDAP is down.
        auth [success=1 default=ignore] pam_unix.so
        auth required pam_ldap.so use_first_pass
        auth required pam_permit.so
The third line is needed, so "success=1" can skip over one module and
still has a module to jump to. Without that, PAM segfaults!

```

Edit: I did a quick check in pam.d and it appears lots of those files include common-auth and then have required statements, usually with pam_limits.so. Using sufficient will therefore by-pass settings in /etc/limits.conf for ldap users.

---


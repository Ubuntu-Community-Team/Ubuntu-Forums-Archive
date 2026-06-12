---
title: "LDAP User can login but local user cannot."
date: 2011-02-27
forum: Security
---

### Post by peridian on 2011-02-27
I followed the Ubuntu guide on how to setup ldap client authentication, but I must have set up the pam.d files incorrectly.

I can login via console/SSH as any ldap user, but if I try to use my original local user admin account, I get access denied.

I think I might have had to leave certain parts of the original files in, instead of replacing them with what is in the guide.

Here's my pam.d files:

```

common-account:

account sufficient                      pam_ldap.so
account required                        pam_unix.so
account requisite                       pam_deny.so
account required                        pam_permit.so

common-auth:

auth    required                        pam_group.so use_first_pass
auth    sufficient                      pam_ldap.so
auth    required                        pam_unix.so nullok_secure use_first_pass
auth    requisite                       pam_deny.so
auth    required                        pam_permit.so

common-password:

password        sufficient                      pam_ldap.so
password        required                        pam_unix.so nullok obscure min=4 max=8 md5
password        requisite                       pam_deny.so
password        required                        pam_permit.so

```

Any help would be appreciated,

Rob.

---


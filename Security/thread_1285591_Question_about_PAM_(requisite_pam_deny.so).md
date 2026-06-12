---
title: "Question about PAM (requisite pam_deny.so)"
date: 2009-10-07
forum: Security
---

### Post by undecim on 2009-10-07
I'm learning how to configure pam.d files by playing around with it on my Arch laptop (yes I have backups), and looking at the default Ubuntu files on my little brother's laptop, and I notice something that I don't understand in Ubuntu's common-auth:

(EDIT: This is from Ubuntu 9.04)
```
auth    [success=1 default=ignore]    pam_unix.so nullok_secure
# here's the fallback if no module succeeds
auth    requisite    pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modiles above will each just jump around.
auth    required    pam_permit.so
[.. and a few more optionals for samba and ecryptfs]
```What I don't understand is why that third line (with pam_deny) doesn't prevent login completely? requisite will cause an immediate failure if the module doesn't succeed, and pam_deny never succeeds.

Also, what is the purpose of requiring pam_permit? According to the comments it will "prime the stack with a positive return value", but isn't that already done if the pam_unix succeeds?

Or am I just completely missing the point?

---

### Post by undecim on 2009-10-09
Ack! Page 2

Bump

---


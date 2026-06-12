---
title: "One-time Passwords and pam_opie"
date: 2008-08-19
forum: Server Platforms
---

### Post by cracker on 2008-08-19
I'm trying to set up one-time passwords on my shell server using the opie-server and opie-client packages. I added pam_opie to my common-auth in /etc/pam.d, and it does challenge me with the information I need. I also can authenticate with it. The problem is, it doesn't change the sequence number. Every log in attempt, it gives me the same sequence number, pass or fail, and therefore is asking for the same password every time. This is obviously a bad thing, and I need to fix it. Does anyone know anything about this?

Below is my /etc/pam.d/common-auth:
```
#
auth    sufficient      pam_unix.so nullok_secure
auth    sufficient      pam_opie.so
auth    optional        pam_smbpass.so migrate missingok
auth    required        pam_deny.so

```

---


---
title: "This incident will be reported"
date: 2008-11-14
forum: Security
---

### Post by sulekha on 2008-11-14
Hi all,

whenever an user who is not in /etc/sudoers file issues the sudo command
we will get the following message

" user is not in the sudoers file.  This incident will be reported"


 now my question is where does this reporting take place ?
 from which file an administrator can know who all tinkered with sudo command ?

---

### Post by jyaan on 2008-11-14
I believe this should be in /var/log/auth.log

For the last three lines:
```
sudo tail /var/log/auth.log

```

---


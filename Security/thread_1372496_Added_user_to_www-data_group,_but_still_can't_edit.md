---
title: "Added user to www-data group, but still can't edit directory with 775"
date: 2010-01-04
forum: Security
---

### Post by samalex on 2010-01-04
Hi,

I'm working in Ubuntu 9.04 Desktop with Apache installed.  I have a directory /var/www/test:
drwxrwxr-x  5 root www-data 4096 2010-01-04 13:51 test

And I've added myself as a member of the group www-data.  Problem though is when i go into /var/www/test I still can't do anything, whether it's creating a new file or directory or editing files there.  The files within the directory are also 775 and setup under group www-data.

Thanks for any suggestions... I'm at a loss though this seems basic.

Sam

---

### Post by samalex on 2010-01-04
Nevermind on this...  Seems logging out and back in fixed the problem.  I thought the settings took effect immediately, so who would've thought.

Take care,

Sam

---

### Post by cdenley on 2010-01-04
> **samalex said:**
> I thought the settings took effect immediately, so who would've thought.

No, looking up group memberships for every single filesystem operation would be very inefficient.
```

id

```

---


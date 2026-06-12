---
title: "sudo: unable to resolve host xyz.xyz"
date: 2009-10-08
forum: Server Platforms
---

### Post by dipen.sutaria on 2009-10-08
sudo: unable to resolve host xyz.xyz

sudo: /etc/mail/sendmail.cf: command not found
user@smprxy-01:~$ No local mailer defined
QueueDirectory (Q) option must be set


i am getting this kind of error message every time when use following command:
"sudo /etc/mail/sendmail.cf"

What could be possible error?

---

### Post by nandemonai on 2009-10-09
> **dipen.sutaria said:**
> sudo: unable to resolve host xyz.xyz

sudo: /etc/mail/sendmail.cf: command not found
user@smprxy-01:~$ No local mailer defined
QueueDirectory (Q) option must be set


i am getting this kind of error message every time when use following command:
"sudo /etc/mail/sendmail.cf"

What could be possible error?

1. Please post your /etc/hosts file

2. If you're trying to edit the sendmail.cf then you need to specify an editor:

```
sudo nano /etc/mail/sendmail.cf
```

---


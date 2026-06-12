---
title: "Hole in Linux kernel provides root rights"
date: 2010-10-22
forum: Security
---

### Post by john_spiral on 2010-10-22
something to worry about?

[http://www.h-online.com/security/news/item/Hole-in-Linux-kernel-provides-root-rights-1122180.html](http://www.h-online.com/security/news/item/Hole-in-Linux-kernel-provides-root-rights-1122180.html)

---

### Post by amauk on 2010-10-22
not if you keep your system up to date

this was fixed more than a week ago

Lucid
[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-lucid.git;a=commit;h=329d37473217c8c7e9062269d69fed42b727d1c5](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-lucid.git;a=commit;h=329d37473217c8c7e9062269d69fed42b727d1c5)

Maverick
[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-maverick.git;a=commit;h=1df5896b4a4de6087f3110c53d2f7fde3617cbe5](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-maverick.git;a=commit;h=1df5896b4a4de6087f3110c53d2f7fde3617cbe5)

---

### Post by anomie on 2010-10-22
If you're using an affected kernel, and can't / won't update at this time, at least employ the workaround the article mentions. 

```
# echo "alias net-pf-21 off" > /etc/modprobe.d/disable-rds
```

---

### Post by cariboo on 2010-10-22
You could always check  [Ubuntu Security Notices]("http://www.ubuntu.com/usn"), if you are concerned.

---


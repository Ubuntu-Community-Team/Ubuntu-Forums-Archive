---
title: "List of checksums for current binaries"
date: 2021-02-09
forum: Security
---

### Post by pmaff on 2021-02-09
Hello,

please be patient if I am asking a question, that has already been answered - I did not find the answer.
I was checking my Ubuntu  18.04.5 LTS with rkhunter and it shows differences to the previous checked Ubuntu 18.04.1 LTS.
My fault: I did not check for a long time. :-(

Is there some list of checksums for current binaries of  Ubuntu  18.04.5 LTS if rkhunter e.g. says:

```
[19:06:54]   /usr/sbin/groupadd                              [ Warning ]
[19:06:54] Warning: The file properties have changed:
[19:06:54]          File: /usr/sbin/groupadd
[19:06:54]          Current hash: d703eec3ce7e9bc44ab21cb5fc7281654b108e145b85d61b88fa05dbfdb10df7
[19:06:54]          Stored hash : 7274989b6b8e7ac8201b85139ed6b32fe2f9c8cc7313e38d2c12c9eee2fa5171
[19:06:54]          Current inode: 398762    Stored inode: 402335
[19:06:54]          Current file modification time: 1553281538 (22-Mär-2019 20:05:38)
[19:06:54]          Stored file modification time : 1516892962 (25-Jän-2018 16:09:22)
```

so that the binaries that should be there are listed and I can compare the warnings?

Thanks in advance.

---

### Post by pmaff on 2021-02-09
Some further search resulted in
[https://ubuntuforums.org/showthread.php?t=2281658&p=13300452#post13300452](https://ubuntuforums.org/showthread.php?t=2281658&p=13300452#post13300452)
which answers my question.

---


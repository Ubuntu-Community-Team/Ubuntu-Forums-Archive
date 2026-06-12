---
title: "evolution always sleeping"
date: 2010-08-22
forum: Server Platforms
---

### Post by hil on 2010-08-22
I use ubuntu 10.1 as my print and file server at home. It's also my workstation for my part time job which requires using Linux. I use evolution to sync to the job's email, contacts, and calendar at Google but evolution's process status is always sleeping. In System monitor which is a GUI of linux command top, I observed the CPU usage went to up 44% on 1 core but the status was still sleeping. Is there a reason why the process was using CPU probably downloading IMAP emails but still sleeping. I read the linux process cycle. When the network resource (downloaded emails) was available for evolution, it should return to running status and process the downloaded emails. Can anyone explain?

```
hil@hilacer:~$ ps -lfe | grep 4050 | grep -v grep
0 [COLOR="Red"]S[/COLOR] hil       4050     1  0  80   0 - 491985 poll_s Aug21 ?       00:09:31 evolution
```

---


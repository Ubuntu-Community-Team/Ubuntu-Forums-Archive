---
title: "crontab -e help"
date: 2008-10-09
forum: Server Platforms
---

### Post by bob444 on 2008-10-09
Hi I'm unable to create/modify any of my crontabs. Every time I try and save the changes it displayed this error message:

```
  [ Error writing /tmp/crontab.MRGbZK/crontab: Permission denied ]

```

I can however read the user crontab,

bob@Bob:~$ crontab -l
0 8 * * * /home/bob/cmd start

I'm really confused and new to Linux/Ubuntu, is there someone who can help me?

Server Edition Ubuntu 8.04 LTS

---

### Post by bob444 on 2008-10-09
could this be down to the permissions in

/var/spool/cron/crontabs 

?

-rw------- 1 root abc     233 2008-10-09 10:18 abc
-rw------- 1 root crontab 232 2008-10-08 14:34 no
-rw------- 1 root crontab 237 2008-10-01 19:45 gs

---


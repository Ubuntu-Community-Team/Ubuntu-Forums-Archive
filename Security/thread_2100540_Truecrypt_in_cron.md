---
title: "Truecrypt in cron"
date: 2013-01-02
forum: Security
---

### Post by lseg on 2013-01-02
Hi,

I would like to add some automatic mounting and dismounting of truecrypt volumes in cron.

I have 2 problems with that:

1) I have to do this as a superuser, in cmd line I just do sudo, but I cant do that in cron. In ubuntu there also is no root user, so how should I achieve this in cron ?
2) I also have to add the Password as plain text, which is not really secure, how can I solve this ?

Kind regards,

Luc

---

### Post by lseg on 2013-01-02
I think I found solution for both questions, please let me know if I am wrong:

1) apparently I can edit the superuser cron by just editing using
sudo crontab -e instead of the regular crontab -e
so all cmds which would typically require sudo to run properly should be stored in this cron.

2)I can put everything in a bash script and then encrypt it by using SHC (not really 100% safe, but it is not plain text anymore).

kind regards,

Luc

---


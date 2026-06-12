---
title: "How do I recreate /var/spool/mail after accidental deletion?"
date: 2010-11-25
forum: Server Platforms
---

### Post by Demented ZA on 2010-11-25
I had the misfortune of running rm -r in my backup of /var just to find out I'm not actually in my backup, but cd'd to /var. :-s Go figure.

I Control+c'd out of it, but only after some damage has been done. I managed to fix everything by comparing to another freshly installed server, however I don't know how to re-create the /var/spool/mail directory as it seems to be a symbolic link. I know how to create symbolic links, but I don't know what i need to link to what.

This is an output of a normal server's /var/spool directory:
```

$ ls -l
total 12
drwxr-xr-x 5 root root 4096 2010-11-22 18:07 cron
lrwxrwxrwx 1 root root    7 2010-11-22 17:42 mail -> ../mail
drwxr-xr-x 2 root root 4096 2010-09-24 14:52 plymouth
drwxrwxrwt 2 root root 4096 2010-10-06 00:25 samba


```Notice the "mail -> ../mail" part. How do I re-create this?

You can all laugh at me [after] you've helped me. Gosh, I feel like such a n00b. Maybe cause I am... lol

Thanks in advance.

---

### Post by HugoSerrano on 2010-11-25
Hi!

#cd /var/spool/
#ln -s ../mail mail

hope it helps! :-)

Tip:

when using **rm -r **do it with full path.
e.g. #rm -r /var/spool/backup

Regards!

---

### Post by Demented ZA on 2011-01-13
Awesome thanks!

I managed to repair all the damage eventually. This helped a LOT!

> **HugoSerrano said:**
> 
  ...
Tip:

when using **rm -r **do it with full path.
e.g. #rm -r /var/spool/backup

Regards!

Good advice!

---


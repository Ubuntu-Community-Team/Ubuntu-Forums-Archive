---
title: "mdadm path not read by cron"
date: 2009-03-17
forum: Server Platforms
---

### Post by arsnova on 2009-03-17
Using Intrepid, I can issue manually mdadm commands, for example:

```
mdadm --misc --detail --test /dev/md0
```

and I can preface this with the path:

```
/sbin/mdadm --misc --detail --test /dev/md0
```

These both give the expected information. Yet, my crontab entry replies to root with "/bin/sh: mdadm: not found." What am I doing incorrectly? For testing purposes, my crontab line is:

```
*/15 * * * * mdadm --misc --detail --test /dev/md0
```

and I've tried committing the path as well:

```
*/15 * * * * /sbin/mdadm --misc --detail --test /dev/md0
```

I'm sure this is something basic, but I'm stumped. Thanks in advance!

---


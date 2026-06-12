---
title: "rsync Host key verification failed."
date: 2013-04-25
forum: Server Platforms
---

### Post by sdmike6 on 2013-04-25
I have a server running Ubuntu Server Precise 12.04.2 LTS

Just a side note this server also authenticates users through OpenLDAP for a samba fileshare.

Ever since I upgraded from 10.04 to 12.04 my rsync cron jobs are failing. If I run the command as the user specified in the cron job it works.

[B]Cron job:
[/B]```
1 01 * * 4 root /usr/bin/rsync -avzP deploy@cldops01.foobar.net:/srv /srv/cldops01-BackUp
```

[B]Error Message:
[/B]```
[FONT=arial]Host key verification failed.[/FONT]
[FONT=arial]rsync: connection unexpectedly closed (0 bytes received so far) [Receiver][/FONT]
[FONT=arial]rsync error: unexplained error (code 255) at io.c(605) [Receiver=3.0.9][/FONT]
```

---

### Post by sdmike6 on 2013-05-02
This issue has been resolved. The issue there was a cookbook in Chef that was writing over my known host file.

---


---
title: "smbd won't start"
date: 2006-09-04
forum: Server Platforms
---

### Post by Coruba67 on 2006-09-04
Hi Guys,

Am trying to serve some files to the other windows PC's on my home network... i know I know... so install Samba and all that jazz... Though it simply won't start

Here's the log entry

[2006/09/04 15:12:15, 0] smbd/server.c:main(847)
smbd version 3.0.23a started.
Copyright Andrew Tridgell and the Samba Team 1992-2006
smbd: symbol lookup error: smbd: undefined symbol: cupsLangDefault


Looking at the second line there it says its started?? Any idea's? How can i get this to startup?

---

### Post by Uluen on 2006-09-04
You sure it's not started? ```
$ ps aux | grep smbd
```
There is some complaining about CUPS in my logs as well but Samba runs just fine.

---


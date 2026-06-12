---
title: "IMAP not starting"
date: 2011-04-28
forum: Server Platforms
---

### Post by Whitedragon150 on 2011-04-28
if i try to start
***@****:~$ service courier-imap restart
 * Stopping Courier IMAP server imapd
Unknown option '-pid='
i can't find where it comes

---

### Post by Whitedragon150 on 2011-04-28
ok i find out that i don't have $PIDFILE but where i get it?

---

### Post by SeijiSensei on 2011-04-28
***You need to run commands like "service" with sudo***.  You can't run them as an ordinary user, just as the administrative ("root") user.  So try:

```

sudo service courier-imap stop
sudo service courier-imap start

```

If that all works, then try "sudo service courier-imap restart" just to make sure.

---

### Post by Whitedragon150 on 2011-04-29
***@******~$ sudo service courier-imap restart
 * Stopping Courier IMAP server imapd
Unknown option '-pid='
and the 
and roundcube not work
edit: roundcube can't connect IMAP server

---


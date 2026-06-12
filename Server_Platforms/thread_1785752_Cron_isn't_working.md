---
title: "Cron isn't working"
date: 2011-06-18
forum: Server Platforms
---

### Post by SpinningAround on 2011-06-18
I'm trying to remotely schedule a shutdown using cron but I can't get it to work. I did setup the following 'sudo crontab -e'

```

20 21 * * * root kill svnserve
30 21 * * * root shutdown -P now

```

For some reason doesn't this work, since I was able to login and get this output when using 'date'
```

sat 18 jun 2011 21.35.46 CEST

```

---

### Post by DaithiF on 2011-06-18
Hi, 
an individual users crontab (including root's) does not have a user field, unlike the system-level crontabs.  So take out 'root' from each of your cron lines and try again.

---

### Post by SpinningAround on 2011-06-20
I tried without user but did not make any difference, is there something else that should be done to get cron to work? I did **only** use crontab -e

---

### Post by HugoSerrano on 2011-06-20
> **SpinningAround said:**
> I tried without user but did not make any difference, is there something else that should be done to get cron to work? I did **only** use crontab -e


Hello

Try:

20 21 * * * killall svnserve 
30 21 * * * shutdown -P now


Do not forguet to leave one empty line in the end of the file.

Regards!

---

### Post by dapperdanny77 on 2011-06-20
you should use the full path for your commands

```

20 21 * * * /usr/bin/killall svnserve

```

cron usually don't have the same environment settings like your login shell. 

```

echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

shows your search path setting. if you're trying to execute a command without the preceding path your shell (bash) is looking for the command in the defined locations.
cron most likely don't have this environment ($PATH) set.

---

### Post by Lars Noodén on 2011-06-21
> **HugoSerrano said:**
> Hello
Do not forguet to leave one empty line in the end of the file.


That is very important.

---

### Post by SeijiSensei on 2011-06-21
The "shutdown" command needs to run with root privileges.  That means you either have to edit root's crontab (sudo crontab -e) or edit the global file /etc/crontab.  If you add the entries to /etc/crontab, they require the username field; if you add them to root's crontab, they don't.

What won't work is adding a shutdown command to an ordinary user's crontab, since ordinary users don't have permission to reboot the machine.

---

### Post by SpinningAround on 2011-06-23
> **HugoSerrano said:**
> Hello

Try:

20 21 * * * killall svnserve 
30 21 * * * shutdown -P now


Do not forguet to leave one empty line in the end of the file.

Regards!

> **dapperdanny77 said:**
> you should use the full path for your commands

```

20 21 * * * /usr/bin/killall svnserve

```

cron usually don't have the same environment settings like your login shell. 

```

echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

shows your search path setting. if you're trying to execute a command without the preceding path your shell (bash) is looking for the command in the defined locations.
cron most likely don't have this environment ($PATH) set.

Adding a newline and giving the full path solved it, thanks everyone :)

---


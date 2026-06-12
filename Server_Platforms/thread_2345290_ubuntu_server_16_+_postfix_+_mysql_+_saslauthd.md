---
title: "ubuntu server 16 + postfix + mysql + saslauthd"
date: 2016-12-02
forum: Server Platforms
---

### Post by daemoncesar on 2016-12-02
I have a problem for weeks.

My server stops authenticating. But when I reboot the saslauthd service (/etc/init.d/saslauthd restart) it works again.



After a few hours, sometimes 2 days the problem reoccurs.

There is a lot of logging, and I can not find the error.

[COLOR=#212121][FONT=arial]After a few hours, sometimes 2 days the problem reoccurs.[/FONT][/COLOR]

---

### Post by alexjpowell on 2016-12-03
run it with -d to run it in the foreground in debug mode

---


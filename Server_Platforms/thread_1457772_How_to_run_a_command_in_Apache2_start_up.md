---
title: "How to run a command in Apache2 start up?"
date: 2010-04-19
forum: Server Platforms
---

### Post by erdanblo on 2010-04-19
Hi,

I need to run a command on apache start up, i'm thinking in edit /etc/init.d/apache2 directly, but i don't know if it's the correct way.

Is it or are there any other way of run a script in apache bootup?

Thank you.

---

### Post by ofn on 2010-04-19
Hi
I think editing /etc/init.d/apache2 is absolutely normal way.
Note: if you want your command to be executed **only on startup** of Apache, than add it in *start* section, after[INDENT][FONT=Courier New]case $1 in[/FONT]
[FONT=Courier New]   start)[/FONT]
[/INDENT]You can also edit /usr/sbin/apache2ctl in similar way, to execute command even on manual startup.

---

### Post by erdanblo on 2010-04-19
I put some commands more at reset and stop section and it works.

Thank you.

---


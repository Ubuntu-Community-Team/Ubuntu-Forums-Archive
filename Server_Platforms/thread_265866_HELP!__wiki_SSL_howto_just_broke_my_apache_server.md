---
title: "HELP!  wiki SSL howto just broke my apache server"
date: 2006-09-26
forum: Server Platforms
---

### Post by kerinin on 2006-09-26
I just finished running through the [SSL]("https://help.ubuntu.com/community/forum/server/apache2/SSL") and [subversion]("http://https://help.ubuntu.com/community/Subversion") howtos on the ubuntu wiki, and when i finished the SSL howto and tried to restart my apache server it failed.  it doesn't even give my any error text, it just says :

```
kerinin@simon:/var/run$ sudo /etc/init.d/apache2 force-reload
 * Forcing reload of apache 2.0 web server...                                [fail]

```

Can somone please help me diagnose this, i sort of need apache to be online...

---

### Post by kerinin on 2006-09-26
*bump*

anybody?

---

### Post by kerinin on 2006-09-26
ok, nevermind

it turns out that when i installed planner, for some reason it installed a log of files in /etc/apache2/sites-enabled, and apache was trying to read them as config files.

strange...

---


---
title: "very weird"
date: 2009-03-09
forum: Security
---

### Post by Svensk023 on 2009-03-09
i found this output this morning in my auth.log

```
Mar  9 07:55:33 josh-xps sudo:     root : TTY=unknown ; PWD=/ ; USER=josh ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Mar  9 07:55:33 josh-xps sudo:     root : TTY=unknown ; PWD=/ ; USER=josh ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Mar  9 07:55:33 josh-xps sudo:     root : TTY=unknown ; PWD=/ ; USER=josh ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
```

i was asleep druing this time, can anybody explain this? is someone trying to use my address as a proxy?

---

### Post by whoop on 2009-03-09
Can you post some information on you network situation as well as services running on your box?
F.i. do you have an ssh server installed, are you running a proxy server, what ports are open on your machine, are you sharing your internet connection etc.

---

### Post by Svensk023 on 2009-03-09
Im running a wired connection that i share with my parents and sister, and while i was sleeping, i had a bit torrent client running, and pidgin.
-no ssh server installed
-no proxy server running
- and ports 2, 3, and 15 are open

---

### Post by cdenley on 2009-03-09
That is the update manager. Nothing to worry about.
/etc/cron.daily/apt
```

# set the proxy based on the admin users gconf settings
admin_user=$(getent group admin|cut -d: -f4|cut -d, -f1)
if [ -n "$admin_user" ] && [ -x /usr/bin/sudo ] && [ -z "$http_proxy" ] && [ -x $
        use=$(sudo -u "$admin_user" gconftool --get /system/http_proxy/use_http_$
        host=$(sudo -u "$admin_user" gconftool --get /system/http_proxy/host)
        port=$(sudo -u "$admin_user" gconftool --get /system/http_proxy/port)
        if [ "$use" = "true" ] && [ -n "$host" ] && [ -n "$port" ]; then
                export http_proxy="http://$host:$port/"
        fi
fi

```
That is actually the root account retrieving the proxy settings of the first admin user by running gconftool as the admin user to use those settings while performing any automated operations like updating the package index.

---

### Post by Svensk023 on 2009-03-09
thank you very much. I got a weird message sent to me during the night on ICQ and so i decided to check my log and noticed root did some stuff that i didnt recognize. but thank you for the clarification!

---

### Post by ssam on 2009-04-26
thanks, i wondered what they might be in my logs.

---


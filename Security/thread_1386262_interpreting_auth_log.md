---
title: "interpreting auth log"
date: 2010-01-20
forum: Security
---

### Post by Fika on 2010-01-20
I am reading the auth logs and find this:

Jan 20 12:57:25 localhost-desktop sudo:     root : TTY=unknown ; PWD=/ ; USER=localhost ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Jan 20 12:57:26 localhost-desktop sudo:     root : TTY=unknown ; PWD=/ ; USER=localhost ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Jan 20 12:57:26 localhost-desktop sudo:     root : TTY=unknown ; PWD=/ ; USER=localhost ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port

I didn't execute these commands. Is this a system thing? 

Thanks for the help

---

### Post by Soul-Sing on 2010-01-20
[HTML]Jan 20 09:56:04 xxxxx-desktop sudo:     root : TTY=unknown ; PWD=/ ; USER=xxxxx ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port[/HTML]

Got these for several years now in my auth.log.

---

### Post by cdenley on 2010-01-20
It is an automated task, for system updates if I remember correctly, checking to see if you have configured your system to use a proxy.

---


---
title: "Bind 9 Cannot Restart"
date: 2016-09-13
forum: Server Platforms
---

### Post by xiaozhupa on 2016-09-13
Hi,

I tried sudo service bind9 restart and it usually works but today there was an error.

Looking at previous threads, I checked my syslog and this is what it shows

 loading configuration from '/etc/bind/named.conf'
 /etc/bind/named.conf.local:44: 'logging' redefined near 'logging'
 loading configuration: already exists
 exiting (due to fatal error)

Can someone assist me in solving this?

Thanks!

---

### Post by newbie-user on 2016-09-13
You probably have set the logging parameters somewhere else in that file or in another file. Check all your conf files for bind to see where you have logging set up.

---


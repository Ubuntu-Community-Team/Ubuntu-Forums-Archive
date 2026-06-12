---
title: "Help! I've broken my lamp!"
date: 2008-10-22
forum: Server Platforms
---

### Post by sTpny on 2008-10-22
Ok, so I was trying to get my lamp server to be accessible from the internet, but something happened, and now I can't even browse my pages locally. I tried  to purge lamp and then reinstall, but that didn't solve anything. I can still get to phpmyadmin, but my own pages, which are in /var/www/MySites, just give a 404 error. Could someone please help me fix this. I've gotten some webspace  from 000hosting, so I don't need to serve to the Internet anymore, but I would still like to continue using my computer as a development platform. Please help.

Tony

---

### Post by cariboo on 2008-10-22
Check the apache2 log files to see what the problem is, in a terminal type:

```
cat /var/log/apache2/error.log | less
```

Jim

---


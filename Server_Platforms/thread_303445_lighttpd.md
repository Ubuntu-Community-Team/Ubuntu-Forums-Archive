---
title: "lighttpd"
date: 2006-11-20
forum: Server Platforms
---

### Post by refaris on 2006-11-20
I am running lighttpd.  It starts and stops with no problems, and the process is definitely running.  There is a file in the document directory... but when I connect to the server's IP... firefox says "unable to connect"

Any ideas?

---

### Post by CyberX on 2006-11-20
You have to edit /etc/lighttpd/lighttpd.conf and comment the server.bind line:

#server.bind = "localhost" 

(but i think the last lighttpd version on edgy doesn't need it anymore)

---


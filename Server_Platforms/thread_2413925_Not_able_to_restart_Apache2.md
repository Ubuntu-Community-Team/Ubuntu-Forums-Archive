---
title: "Not able to restart Apache2"
date: 2019-03-04
forum: Server Platforms
---

### Post by pipa2 on 2019-03-04
Hi There,

I'm running Ubuntu 18.04 and having trouble restarting Apache2. Have executed "[COLOR=#242729][FONT=Consolas]systemctl status --no-pager --full apache2"  [/FONT][/COLOR]uand coming with the following error(As per below). Looks like I have some socket already in use or something. 

Does anyone know how to look at this and where, so I can fix it?

Regards,

Pipa



```
Mar 04 15:32:34 valdivia apachectl[5495]: AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message
Mar 04 15:32:34 valdivia apachectl[5495]: (98)Address already in use: AH00072: make_sock: could not bind to address [::]:80
Mar 04 15:32:34 valdivia apachectl[5495]: (98)Address already in use: AH00072: make_sock: could not bind to address 0.0.0.0:80
Mar 04 15:32:34 valdivia apachectl[5495]: no listening sockets available, shutting down
Mar 04 15:32:34 valdivia apachectl[5495]: AH00015: Unable to open logs
Mar 04 15:32:34 valdivia apachectl[5495]: Action 'start' failed.
Mar 04 15:32:34 valdivia apachectl[5495]: The Apache error log may have more information.
Mar 04 15:32:34 valdivia systemd[1]: apache2.service: Control process exited, code=exited status=1
Mar 04 15:32:34 valdivia systemd[1]: apache2.service: Failed with result 'exit-code'.
Mar 04 15:32:34 valdivia systemd[1]: Failed to start The Apache HTTP Server.
```

---

### Post by lisati on 2019-03-04
*Thread moved to **Server Platforms**.*

---


---
title: "logrotate named"
date: 2006-08-09
forum: Server Platforms
---

### Post by hogman23 on 2006-08-09
Guys,
I need to setup logrotate to rotate my named logs.  I have named.log, lame.log, etc.  Is anyone doing this?  Can someone tell me how to accomplish it?
Thanks

---

### Post by hogman23 on 2006-08-09
Ok, I figured it out.  For anyone wanting to do this, go to /etc/logrotate.conf and add the following, editing the log locations to wherever they are being written.

/var/log/named/*         {
     daily
     rotate 1
     missingok
   # postrotate
   #     /bin/kill -HUP `cat /var/run/named.pid 2> /dev/null` 2> /dev/null || true
   # endscript
}

---


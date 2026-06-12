---
title: "Apache2 problem when starting server"
date: 2015-10-28
forum: Server Platforms
---

### Post by Riccardo_Ferrarett on 2015-10-28
Hello,

I'm having a problem on my home server with apache. After a reboot it doesn't start, but if i do manually

```

root@raspbx:~#  /etc/init.d/apache2 restart
[....] Restarting web server: apache2AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1. Set the 'ServerName' directive globally to suppress this message
. ok
root@raspbx:~#

```

This is what I get into error.log before starting it manually (just rebooted)

```
[Wed Oct 28 16:34:06.196714 2015] [mpm_prefork:notice] [pid 8582] AH00163: Apache/2.4.10 (Raspbian) configured -- resuming normal operations[Wed Oct 28 16:34:06.197588 2015] [core:notice] [pid 8582] AH00094: Command line: '/usr/sbin/apache2'
[Wed Oct 28 16:34:09.326511 2015] [mpm_prefork:notice] [pid 8582] AH00169: caught SIGTERM, shutting down
[Wed Oct 28 16:34:11.355594 2015] [mpm_prefork:notice] [pid 8681] AH00163: Apache/2.4.10 (Raspbian) configured -- resuming normal operations
[Wed Oct 28 16:34:11.355981 2015] [core:notice] [pid 8681] AH00094: Command line: '/usr/sbin/apache2'
[Wed Oct 28 16:34:43.827798 2015] [mpm_prefork:notice] [pid 8681] AH00169: caught SIGTERM, shutting down



```

This is a non blocking issue but I want to understand why
Thanks in advance for help

---

### Post by Habitual on 2015-10-28
It's only a waring. It can be ignored.
But type As like myself just won't let that be.
so...
```
echo "ServerName localhost" >> /etc/apache2/apache2.conf
```

then restart. check for Warning.

---

### Post by Riccardo_Ferrarett on 2015-10-28
Thanks but this not answers to the main question
I wish it running at boot, and avoid to type manually [COLOR=#000000][FONT=Ubuntu Mono]/etc/init.d/apache2 restart

Thanks in advance[/FONT][/COLOR]

---


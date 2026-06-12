---
title: "Internal Server Error 500 upon activation of a WordPress plugin"
date: 2015-03-30
forum: Server Platforms
---

### Post by zkvvoob on 2015-03-30
Hello,

I have an Ubuntu 14.04 server where a WordPress website generates an Internal Error 500 every time I activate the BuddyPress plugin. This is the actual error:


```
[Sat Mar 28 19:12:28.102868 2015] [fastcgi:error] [pid 10447] (104)Connection reset by peer: [client 192.168.1.1:55431] FastCGI: comm with server "/var/www/clients/client1/web4/cgi-bin/php5-fcgi-*-80-site.eu" aborted: read failed, referer: http://site.eu/wp-admin/update.php?action=install-plugin&plugin=buddypress&_wpnonce=54e15a2310


[Sat Mar 28 19:12:28.103055 2015] [fastcgi:error] [pid 10447] [client 192.168.1.1:55431] FastCGI: incomplete headers (0 bytes) received from server "/var/www/clients/client1/web4/cgi-bin/php5-fcgi-*-80-site.eu", referer: http://site.eu/wp-admin/update.php?action=install-plugin&plugin=buddypress&_wpnonce=54e15a2310
```


The strange thing is that before, when the server was running Ubuntu 12, I had no troubles activating and using BuddyPress. Then something possessed me and I decided to upgrade the OS to 14.04 and as a result the site became inaccessible. Finally, I figured that it was BuddyPress that was causing the issue, removed it from the plugins folder and the site went back to working. Now every time I try to re-add BP, I get the error above.

Could you help me find out what's causing this and how to get everything back to normal?

Thank you!

---

### Post by SeijiSensei on 2015-03-30
I'd be suspicious of this line:
```
FastCGI: comm with server "/var/www/clients/client1/web4/cgi-bin/php5-fcgi-*-80-site.eu" aborted:
```
The asterisk works at the command line, but it doesn't seem correct in this instance.

---

### Post by zkvvoob on 2015-03-30
To be honest, I'm suspicious of everything because I'm quite new to the Ubuntu arena. In other words, I don't really know how to troubleshoot this issue. Any and all help is appreciated greatly.

---


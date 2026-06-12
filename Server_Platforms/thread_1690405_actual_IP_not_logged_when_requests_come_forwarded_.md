---
title: "actual IP not logged when requests come forwarded by a reverse proxy"
date: 2011-02-18
forum: Server Platforms
---

### Post by tapas_mishra on 2011-02-18
My apache2.conf
[http://pastebin.com/uTVKt1wD](http://pastebin.com/uTVKt1wD)
and apache vhost file
[http://pastebin.com/QDd3LDZ4](http://pastebin.com/QDd3LDZ4)
the apche2.conf and vhost file I gave the link are the machine on LAN
where site is actually hosted.
When some one from internet access the site then I expect a log of IP in
access.log
instead of which I see the IP of machine which is working as Reverse
Proxy server for all such requests.
What mistake did I do above.

---

### Post by dtfinch on 2011-02-18
My guess would be to change "combined" to "vhost_combined" on the customlog line of your vhost file, which should add the X-Forwarded-For header value to the log.

---

### Post by rudelgurke on 2011-02-18
[http://stderr.net/apache/rpaf/](http://stderr.net/apache/rpaf/) will help with this issue :)

---

### Post by tapas_mishra on 2011-02-21
while compiling rpaf I got following

> apxs -i -c -n mod_rpaf-2.0.so mod_rpaf-2.0.c
No command 'apxs' found, did you mean:
 Command 'apbs' from package 'apbs' (universe)
 Command 'axs' from package 'afnix' (universe)
 Command 'apxs2' from package 'apache2-threaded-dev' (main)
 Command 'apxs2' from package 'apache2-prefork-dev' (main)


---

### Post by tapas_mishra on 2011-02-21
> **dtfinch said:**
> My guess would be to change "combined" to "vhost_combined" on the customlog line of your vhost file, which should add the X-Forwarded-For header value to the log.

You were right.It has worked now.

---


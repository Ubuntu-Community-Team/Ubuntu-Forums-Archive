---
title: "Slow internet out of nowhere"
date: 2017-09-06
forum: Server Platforms
---

### Post by tottel on 2017-09-06
Hopefully this is the right place to ask, I've been going at this one for days and I can't solve/fix it..

[COLOR=#111111][FONT=Ubuntu]In short:

My websites (Running Nginx + Apache thru VestaCP) has become insanely slow out of nowhere. Every now and then they don't even respond, which gives me that CloudFlare page which tells you the host is offline.
Everything else on the network is working perfectly fine. I've even ran a full system check using HP's tool [/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu](All hardware passed) [/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]and reinstalled the server entirely by now, including changed network port on the computer (Got 2). Still the same problem.
It's a home server and it's been running fine for over 3 years.

I'm not very familiar with network problems, so I got very little experience troubleshooting this.

Nginx error.log
```
[/FONT][/COLOR]2017/09/06 16:58:53 [error] 41514#0: *210 FastCGI sent in stderr: "PHP message: PHP Notice:  Undefined index: HTTP_CLIENT_IP in /usr/local/vesta$PHP message: PHP Notice:  Undefined index: HTTP_X_FORWARDED_FOR in /usr/local/vesta/web/inc/main.php on line 14
PHP message: PHP Notice:  Undefined index: HTTP_X_FORWARDED in /usr/local/vesta/web/inc/main.php on line 14
PHP message: PHP Notice:  Undefined index: HTTP_FORWARDED_FOR in /usr/local/vesta/web/inc/main.php on line 14

PHP message: PHP Notice:  Undefined index: HTTP_FORWARDED in /usr/local/vesta/web/inc/main.php on line 14" while reading response header from up$[COLOR=#111111][FONT=Ubuntu]
```


Apache error.log
```
[/FONT][/COLOR][Wed Sep 06 17:15:55.883843 2017] [:notice] [pid 56328] mod_ruid2/0.9.8 enabled
[Wed Sep 06 17:15:55.884688 2017] [mpm_prefork:notice] [pid 56328] AH00163: Apache/2.4.18 (Ubuntu) mod_fcgid/2.3.9 OpenSSL/1.0.2g configured -- $
[Wed Sep 06 17:15:55.884704 2017] [core:notice] [pid 56328] AH00094: Command line: '/usr/sbin/apache2'
[Wed Sep 06 17:16:03.378958 2017] [mpm_prefork:notice] [pid 56328] AH00171: Graceful restart requested, doing restart
[Wed Sep 06 17:16:03.490971 2017] [:notice] [pid 56328] mod_ruid2/0.9.8 enabled
[Wed Sep 06 17:16:03.491803 2017] [mpm_prefork:notice] [pid 56328] AH00163: Apache/2.4.18 (Ubuntu) mod_fcgid/2.3.9 OpenSSL/1.0.2g configured -- $
[Wed Sep 06 17:16:03.491818 2017] [core:notice] [pid 56328] AH00094: Command line: '/usr/sbin/apache2'
[COLOR=#111111][FONT=Ubuntu]
```

[/FONT][/COLOR]

---

### Post by costa_g on 2017-09-07
Could you post an update of your error logs if you have not solved this yet? It could be useful.

---


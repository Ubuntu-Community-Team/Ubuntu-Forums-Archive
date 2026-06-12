---
title: "Problem restarting apache2"
date: 2015-08-17
forum: Server Platforms
---

### Post by Rui_Brcia on 2015-08-17
Hi,

Ubuntu Server 15.04

I am trying to reload/restart my apache2 services and there is errors:

services apache2 reload: Job for apache2.service invalid.
services apache2 restart: Job for apache2.service failed. See "systemctl status apache2.service" and "journalctl -xe" for details.

[B]systemctl status apache2.service
[/B]apache2.service - LSB: Apache2 web server
Loaded: loaded (/etc/init.d/apache2)
Active: failed (Result: exit-code) since Tue 2015-08-18 01:39:33 CEST; 51s ago
Docs: man:systemd-sysv-generator(8)
Process: 1971 ExecStart=/etc/init.d/apache2 start (code=exited, status=1/FAILURE)&#8203;

[B]journalctl -xe
[/B]-- Unit apache2.service has begun starting up.
Aug 18 01:41:40 xpto apache2[2013]: * Starting web server apache2
Aug 18 01:41:41 xpto apache2[2013]: *
Aug 18 01:41:41 xpto apache2[2013]: * The apache2 configtest failed.
Aug 18 01:41:41 xpto apache2[2013]: Output of config test was:
Aug 18 01:41:41 xpto apache2[2013]: apache2: Syntax error on line 219 of /etc/apache2/apache2.conf: Synt
Aug 18 01:41:41 xpto apache2[2013]: Action 'configtest' failed.
Aug 18 01:41:41 xpto apache2[2013]: The Apache error log may have more information.
Aug 18 01:41:41 xpto systemd[1]: apache2.service: control process exited, code=exited status=1
Aug 18 01:41:41 xpto systemd[1]: Failed to start LSB: Apache2 web server.
-- Subject: Unit apache2.service has failed
-- Defined-By: systemd
-- Support: [http://lists.freedesktop.org/mailman/listinfo/systemd-devel](http://lists.freedesktop.org/mailman/listinfo/systemd-devel)

so what can i do to fix this errors ?
I have seen the line 219 that is: IncludeOptional sites-enabled/*.conf
Best Regards

---

### Post by sandyd on 2015-08-17
Moved to *Server Platforms*

---

### Post by nerdtron on 2015-08-18
What did you edited before you needed to restart apache?

> I have seen the line 219 that is: IncludeOptional sites-enabled/*.conf
It could mean that you have a syntax error even before line 219. Check the config again and look if you have a typo, you could have accidentally uncommented a comment line or you could have erased some symbols like the </IfModule>

Then after checking the config, run the apache config test. It is always a good idea to run configtest everytime you make changes to the apace config file so that you won't accidentally stop apache. Post the output here.
```
 sudo apache2ctl configtest
```

---

### Post by Rui_Brcia on 2015-08-18
Hi,

I have run that command and in fact there was a missing ">"
Then i run again and "Syntax OK". Rerun reload and errors still happen but then i try to restart and all went OK.

Thanks for helping and for that command, its a god one :D

---


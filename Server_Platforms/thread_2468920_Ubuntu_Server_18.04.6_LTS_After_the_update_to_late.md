---
title: "Ubuntu Server 18.04.6 LTS: After the update to latest apache version, segfault"
date: 2021-11-14
forum: Server Platforms
---

### Post by bonzo123 on 2021-11-14
After updating to the latest version of Ubuntu 18.04.6 LTS, apache doesn't start anymore. 
I get this error:
```
 	[FONT=monospace][COLOR=#ff5454]**&#9679;**[/COLOR][COLOR=#000000] apache2.service - The Apache HTTP Server [/COLOR]
   Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled) 
  Drop-In: /lib/systemd/system/apache2.service.d 
           &#9492;&#9472;apache2-systemd.conf 
   Active: [COLOR=#ff5454]**failed**[/COLOR][COLOR=#000000] (Result: exit-code) since Sun 2021-11-14 20:26:58 CET; 11s ago [/COLOR]
  Process: 2966 ExecStart=/usr/sbin/apachectl start [COLOR=#ff5454]**(code=exited, status=139)**[/COLOR]

Nov 14 20:26:58 web003 systemd[1]: Starting The Apache HTTP Server... 
Nov 14 20:26:58 web003 apachectl[2966]: /usr/sbin/apachectl: line 162:  2982 Segmentation fault      (core dumped) ${HTTPD} ${APACHE_ARGUMENTS} -k "${ARGV}" 
Nov 14 20:26:58 web003 apachectl[2966]: Action 'start' failed. 
Nov 14 20:26:58 web003 apachectl[2966]: The Apache error log may have more information. 
Nov 14 20:26:58 web003 systemd[1]: [COLOR=#000000]**apache2.service: Control process exited, code=exited status=139**[/COLOR]
Nov 14 20:26:58 web003 systemd[1]: [COLOR=#000000]**apache2.service: Failed with result 'exit-code'.**[/COLOR]
Nov 14 20:26:58 web003 systemd[1]: [COLOR=#ff5454]**Failed to start The Apache HTTP Server.**[/COLOR]
[/FONT]
```

The server was hosted as a live VPS on kvm, I've downloaded it as  qcow2 and imported it into virtualbox and kvm on my local computer. The  error stays the same so a hardware error is unlikely
Other than the standard sources for apt I also have ondrejs php repository so I can run different php versions at the same time
If I hold back the update for apache (with apt-mark) the update updates everything and apache starts normally
Maybe it helps even if it's not related to apache, but if I try to do a  release upgrade to Ubuntu 20-something LTS it breaks as well.  Segmentation fault in python. So not even an upgrade to a new release  helps

enabled mods
```
[FONT=monospace]lrwxrwxrwx 1 root root   34 Sep 27  2019 [COLOR=#54ffff]**apache2-doc.conf**[/COLOR][COLOR=#000000] -> ../conf-available/apache2-doc.conf [/COLOR]
lrwxrwxrwx 1 root root   30 Sep 27  2019 [COLOR=#54ffff]**charset.conf**[/COLOR][COLOR=#000000] -> ../conf-available/charset.conf [/COLOR]
lrwxrwxrwx 1 root root   30 Sep 27  2019 [COLOR=#54ffff]**httpoxy.conf**[/COLOR][COLOR=#000000] -> ../conf-available/httpoxy.conf [/COLOR]
lrwxrwxrwx 1 root root   44 Sep 27  2019 [COLOR=#54ffff]**localized-error-pages.conf**[/COLOR][COLOR=#000000] -> ../conf-available/localized-error-pages.conf [/COLOR]
lrwxrwxrwx 1 root root   46 Sep 27  2019 [COLOR=#54ffff]**other-vhosts-access-log.conf**[/COLOR][COLOR=#000000] -> ../conf-available/other-vhosts-access-log.conf [/COLOR]
lrwxrwxrwx 1 root root   33 Sep 27  2019 [COLOR=#54ffff]**phpmyadmin.conf**[/COLOR][COLOR=#000000] -> ../conf-available/phpmyadmin.conf [/COLOR]
lrwxrwxrwx 1 root root   32 Nov  4  2020 [COLOR=#54ffff]**roundcube.conf**[/COLOR][COLOR=#000000] -> ../conf-available/roundcube.conf [/COLOR]
lrwxrwxrwx 1 root root   31 Sep 27  2019 [COLOR=#54ffff]**security.conf**[/COLOR][COLOR=#000000] -> ../conf-available/security.conf [/COLOR]
lrwxrwxrwx 1 root root   36 Sep 27  2019 [COLOR=#54ffff]**serve-cgi-bin.conf**[/COLOR][COLOR=#000000] -> ../conf-available/serve-cgi-bin.conf[/COLOR][/FONT]
```

enabled confs
```
[FONT=monospace][COLOR=#000000]lrwxrwxrwx 1 root root   36 Sep 27  2019 [/COLOR][COLOR=#54ffff]**access_compat.load**[/COLOR][COLOR=#000000] -> ../mods-available/access_compat.load
[/COLOR]
lrwxrwxrwx 1 root root   30 Sep 27  2019 [COLOR=#54ffff]**actions.conf**[/COLOR][COLOR=#000000] -> ../mods-available/actions.conf
[/COLOR]
lrwxrwxrwx 1 root root   30 Sep 27  2019 [COLOR=#54ffff]**actions.load**[/COLOR][COLOR=#000000] -> ../mods-available/actions.load
[/COLOR]
lrwxrwxrwx 1 root root   28 Sep 27  2019 [COLOR=#54ffff]**alias.conf**[/COLOR][COLOR=#000000] -> ../mods-available/alias.conf
[/COLOR]
lrwxrwxrwx 1 root root   28 Sep 27  2019 [COLOR=#54ffff]**alias.load**[/COLOR][COLOR=#000000] -> ../mods-available/alias.load
[/COLOR]
lrwxrwxrwx 1 root root   33 Sep 27  2019 [COLOR=#54ffff]**auth_basic.load**[/COLOR][COLOR=#000000] -> ../mods-available/auth_basic.load
[/COLOR]
lrwxrwxrwx 1 root root   33 Sep 27  2019 [COLOR=#54ffff]**authn_core.load**[/COLOR][COLOR=#000000] -> ../mods-available/authn_core.load
[/COLOR]
lrwxrwxrwx 1 root root   33 Sep 27  2019 [COLOR=#54ffff]**authn_file.load**[/COLOR][COLOR=#000000] -> ../mods-available/authn_file.load
[/COLOR]
lrwxrwxrwx 1 root root   33 Sep 27  2019 [COLOR=#54ffff]**authz_core.load**[/COLOR][COLOR=#000000] -> ../mods-available/authz_core.load
[/COLOR]
lrwxrwxrwx 1 root root   33 Sep 27  2019 [COLOR=#54ffff]**authz_host.load**[/COLOR][COLOR=#000000] -> ../mods-available/authz_host.load
[/COLOR]
lrwxrwxrwx 1 root root   33 Sep 27  2019 [COLOR=#54ffff]**authz_user.load**[/COLOR][COLOR=#000000] -> ../mods-available/authz_user.load
[/COLOR]
lrwxrwxrwx 1 root root   32 Sep 27  2019 [COLOR=#54ffff]**autoindex.conf**[/COLOR][COLOR=#000000] -> ../mods-available/autoindex.conf
[/COLOR]
lrwxrwxrwx 1 root root   32 Sep 27  2019 [COLOR=#54ffff]**autoindex.load**[/COLOR][COLOR=#000000] -> ../mods-available/autoindex.load
[/COLOR]
lrwxrwxrwx 1 root root   30 Sep 27  2019 [COLOR=#54ffff]**deflate.conf**[/COLOR][COLOR=#000000] -> ../mods-available/deflate.conf
[/COLOR]
lrwxrwxrwx 1 root root   30 Sep 27  2019 [COLOR=#54ffff]**deflate.load**[/COLOR][COLOR=#000000] -> ../mods-available/deflate.load
[/COLOR]
lrwxrwxrwx 1 root root   26 Sep 27  2019 [COLOR=#54ffff]**dir.conf**[/COLOR][COLOR=#000000] -> ../mods-available/dir.conf
[/COLOR]
lrwxrwxrwx 1 root root   26 Sep 27  2019 [COLOR=#54ffff]**dir.load**[/COLOR][COLOR=#000000] -> ../mods-available/dir.load
[/COLOR]
lrwxrwxrwx 1 root root   26 Sep 27  2019 [COLOR=#54ffff]**env.load**[/COLOR][COLOR=#000000] -> ../mods-available/env.load
[/COLOR]
lrwxrwxrwx 1 root root   28 Sep 27  2019 [COLOR=#54ffff]**fcgid.conf**[/COLOR][COLOR=#000000] -> ../mods-available/fcgid.conf
[/COLOR]
lrwxrwxrwx 1 root root   28 Sep 27  2019 [COLOR=#54ffff]**fcgid.load**[/COLOR][COLOR=#000000] -> ../mods-available/fcgid.load
[/COLOR]
lrwxrwxrwx 1 root root   29 Sep 27  2019 [COLOR=#54ffff]**filter.load**[/COLOR][COLOR=#000000] -> ../mods-available/filter.load
[/COLOR]
lrwxrwxrwx 1 root root   27 Sep 27  2019 [COLOR=#54ffff]**mime.conf**[/COLOR][COLOR=#000000] -> ../mods-available/mime.conf
[/COLOR]
lrwxrwxrwx 1 root root   27 Sep 27  2019 [COLOR=#54ffff]**mime.load**[/COLOR][COLOR=#000000] -> ../mods-available/mime.load
[/COLOR]
lrwxrwxrwx 1 root root   34 Sep 27  2019 [COLOR=#54ffff]**mpm_prefork.conf**[/COLOR][COLOR=#000000] -> ../mods-available/mpm_prefork.conf
[/COLOR]
lrwxrwxrwx 1 root root   34 Sep 27  2019 [COLOR=#54ffff]**mpm_prefork.load**[/COLOR][COLOR=#000000] -> ../mods-available/mpm_prefork.load
[/COLOR]
lrwxrwxrwx 1 root root   34 Sep 27  2019 [COLOR=#54ffff]**negotiation.conf**[/COLOR][COLOR=#000000] -> ../mods-available/negotiation.conf
[/COLOR]
lrwxrwxrwx 1 root root   34 Sep 27  2019 [COLOR=#54ffff]**negotiation.load**[/COLOR][COLOR=#000000] -> ../mods-available/negotiation.load
[/COLOR]
lrwxrwxrwx 1 root root   29 Sep 27  2019 [COLOR=#54ffff]**php7.3.conf**[/COLOR][COLOR=#000000] -> ../mods-available/php7.3.conf
[/COLOR]
lrwxrwxrwx 1 root root   29 Sep 27  2019 [COLOR=#54ffff]**php7.3.load**[/COLOR][COLOR=#000000] -> ../mods-available/php7.3.load
[/COLOR]
lrwxrwxrwx 1 root root   28 Sep 27  2019 [COLOR=#54ffff]**proxy.conf**[/COLOR][COLOR=#000000] -> ../mods-available/proxy.conf
[/COLOR]
lrwxrwxrwx 1 root root   33 Sep 27  2019 [COLOR=#54ffff]**proxy_fcgi.load**[/COLOR][COLOR=#000000] -> ../mods-available/proxy_fcgi.load
[/COLOR]
lrwxrwxrwx 1 root root   28 Sep 27  2019 [COLOR=#54ffff]**proxy.load**[/COLOR][COLOR=#000000] -> ../mods-available/proxy.load
[/COLOR]
lrwxrwxrwx 1 root root   29 Sep 27  2019 [COLOR=#54ffff]**python.load**[/COLOR][COLOR=#000000] -> ../mods-available/python.load
[/COLOR]
lrwxrwxrwx 1 root root   33 Sep 27  2019 [COLOR=#54ffff]**reqtimeout.conf**[/COLOR][COLOR=#000000] -> ../mods-available/reqtimeout.conf
[/COLOR]
lrwxrwxrwx 1 root root   33 Sep 27  2019 [COLOR=#54ffff]**reqtimeout.load**[/COLOR][COLOR=#000000] -> ../mods-available/reqtimeout.load
[/COLOR]
lrwxrwxrwx 1 root root   30 Dec 18  2019 [COLOR=#54ffff]**rewrite.load**[/COLOR][COLOR=#000000] -> ../mods-available/rewrite.load
[/COLOR]
lrwxrwxrwx 1 root root   31 Sep 27  2019 [COLOR=#54ffff]**setenvif.conf**[/COLOR][COLOR=#000000] -> ../mods-available/setenvif.conf
[/COLOR]
lrwxrwxrwx 1 root root   31 Sep 27  2019 [COLOR=#54ffff]**setenvif.load**[/COLOR][COLOR=#000000] -> ../mods-available/setenvif.load
[/COLOR]
lrwxrwxrwx 1 root root   36 Sep 27  2019 [COLOR=#54ffff]**socache_shmcb.load**[/COLOR][COLOR=#000000] -> ../mods-available/socache_shmcb.load
[/COLOR]
lrwxrwxrwx 1 root root   26 Sep 27  2019 [COLOR=#54ffff]**ssl.conf**[/COLOR][COLOR=#000000] -> ../mods-available/ssl.conf
[/COLOR]
lrwxrwxrwx 1 root root   26 Sep 27  2019 [COLOR=#54ffff]**ssl.load**[/COLOR][COLOR=#000000] -> ../mods-available/ssl.load
[/COLOR]
lrwxrwxrwx 1 root root   29 Sep 27  2019 [COLOR=#54ffff]**status.conf**[/COLOR][COLOR=#000000] -> ../mods-available/status.conf
[/COLOR]
lrwxrwxrwx 1 root root   29 Sep 27  2019 [COLOR=#54ffff]**status.load**[/COLOR][COLOR=#000000] -> ../mods-available/status.load
[/COLOR]
lrwxrwxrwx 1 root root   29 Sep 27  2019 [COLOR=#54ffff]**suexec.load**[/COLOR][COLOR=#000000] -> ../mods-available/suexec.load[/COLOR]


[/FONT]
```

---


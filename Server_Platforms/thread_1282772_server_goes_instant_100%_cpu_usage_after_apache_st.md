---
title: "server goes instant 100% cpu usage after apache start"
date: 2009-10-04
forum: Server Platforms
---

### Post by exww on 2009-10-04
Hello 
I have been running apache server for a few months and today i get a huge problem.
My website droped and i went to check what was going on, so i typed the "top" command and i see that theres like endless ammount of user "nobody" using the cpu and the command they use is :
```
/opt/lampp/bin/httpd -k start -DSSL -DPHP5 -E /opt/lampp/logs/error_log
```If i go to check that log i get


```

[Mon Oct 05 01:13:12 2009] [notice] suEXEC mechanism enabled (wrapper: /opt/lampp/bin/suexec)
[Mon Oct 05 01:13:13 2009] [warn] RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Mon Oct 05 01:13:13 2009] [warn] RSA server certificate CommonName (CN) `localhost' does NOT match server name!?
[Mon Oct 05 01:13:13 2009] [notice] Digest: generating secret for digest authentication ...
[Mon Oct 05 01:13:13 2009] [notice] Digest: done
[Mon Oct 05 01:13:14 2009] [warn] RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Mon Oct 05 01:13:14 2009] [warn] RSA server certificate CommonName (CN) `localhost' does NOT match server name!?
[Mon Oct 05 01:13:14 2009] [notice] Apache/2.2.11 (Unix) DAV/2 mod_ssl/2.2.11 OpenSSL/0.9.8k PHP/5.2.9 mod_apreq2-20051231/2.6.0 mod_perl/2.0.4 Perl/v5.10.0 configured -- resuming normal operations

```Any help would be appriciated

edit: i have checked the status of mysql and its getting alot of "select" requests(select 1,866 14.83k 73.44%)  and alot of other stuff aswell is in red

---


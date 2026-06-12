---
title: "apache problem"
date: 2009-06-28
forum: Server Platforms
---

### Post by jazztrump9 on 2009-06-28
im getting the httpd dead but subsys still locked error when i type service httpd status. I tried removing /var/lock/subsys/httpd and i removed the httpd.pid but that didn't help. when i view the error log from httpd i see the following:
 
 
 
[Sun Jun 28 05:29:07 2009] [notice] core dump file size limit raised to 4294967295 bytes
[Sun Jun 28 05:29:07 2009] [notice] suEXEC mechanism enabled (wrapper: /usr/sbin/suexec)
[Sun Jun 28 05:29:09 2009] [notice] ModSecurity for Apache/2.5.9 ([[COLOR=#000000]http://www.modsecurity.org/[/COLOR]]("http://www.modsecurity.org/")) configured.
[Sun Jun 28 05:29:09 2009] [notice] Original server signature: Apache/2.2.11 (Fedora)
[Sun Jun 28 05:29:09 2009] [notice] Digest: generating secret for digest authentication ...
[Sun Jun 28 05:29:09 2009] [notice] Digest: done
[Sun Jun 28 05:29:11 2009] [notice] mod_python: Creating 4 session mutexes based on 150 max processes and 0 max threads.
[Sun Jun 28 05:29:11 2009] [notice] mod_python: using mutex_directory /tmp 
[Sun Jun 28 05:29:12 2009] [notice] Apache/2.2.11 (Unix) DAV/2 mod_auth_kerb/5.4 mod_auth_pgsql/2.0.3 mod_ssl/2.2.11 OpenSSL/0.9.8k-fips Apache/2.2.0 (Fedora) PHP/5.2.9 mod_python/3.3.1 Python/2.6 mod_perl/2.0.4 Perl/v5.10.0 configured -- resuming normal operations
[Sun Jun 28 05:37:29 2009] [notice] caught SIGTERM, shutting down
[Sun Jun 28 05:40:54 2009] [notice] core dump file size limit raised to 4294967295 bytes
[Sun Jun 28 05:40:56 2009] [notice] ModSecurity for Apache/2.5.9 ([[COLOR=#000000]http://www.modsecurity.org/[/COLOR]]("http://www.modsecurity.org/")) configured.
[Sun Jun 28 05:40:56 2009] [notice] Original server signature: Apache/2.2.11 (Fedora)
[Sun Jun 28 05:40:57 2009] [notice] Digest: generating secret for digest authentication ...
[Sun Jun 28 05:40:57 2009] [notice] Digest: done
[Sun Jun 28 05:40:58 2009] [notice] mod_python: Creating 4 session mutexes based on 150 max processes and 0 max threads.
[Sun Jun 28 05:40:58 2009] [notice] mod_python: using mutex_directory /tmp 
[Sun Jun 28 05:40:59 2009] [notice] Apache/2.2.11 (Unix) DAV/2 mod_auth_kerb/5.4 mod_auth_pgsql/2.0.3 mod_ssl/2.2.11 OpenSSL/0.9.8k-fips Apache/2.2.0 (Fedora) PHP/5.2.9 mod_python/3.3.1 Python/2.6 mod_perl/2.0.4 Perl/v5.10.0 configured -- resuming normal operations
 
i can start the service and it actually is running, but i cant stop it unless i do a killall httpd and restarting doesn't work, i have to kill it and start it again. Although the server is running and doing everything its supposed to, i somehow dont think its working 100% the way it should because of that error.
 
I hope someone has some insight on this.

---

### Post by Vegan on 2009-06-28
Looks like you have some configuration that is unorthodox compared to my setup.

I have the basic LAMP with several additional tasks such as Java and other programming languages.

My web sites are all PHP and it works fine. I have not yet tried ASP even though I have the mono-project installed.

try....

```

sudo touch /forcefsck
sudo reboot

```

and see if that helps

then...

```

sudo apt-get update
sudo apt-get upgrade

```

and see if the updates helps

---


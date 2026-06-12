---
title: "Apache Starting Over And Over Crashing the server"
date: 2014-12-25
forum: Server Platforms
---

### Post by april4 on 2014-12-25
Happy Holidays!!  Newbie here and I need a little help.  I have a server that is running Apache and MySQL on Ubuntu... The server keeps going unaccessable via SSH and APache and MySQL shut down.  I can only get in via the console when this happens.  I have to always do reboot to get it running again and it only stays on for about a day before going down again.  I installed htop to see if I could figure it out.  What I see is /usr/sbin/apache -k start every 10 - 15 seconds.  I don't think that apache is supposed to be started over and over again, right?  How do I track down what is doing this?  Any help is appreciated.

---

### Post by Sef on 2014-12-25
Moved to server platform

---

### Post by MAFoElffen on 2014-12-26
Please post your /var/log/apache2/error.log file. That may shed some light on this.

---

### Post by april4 on 2014-12-26
Here id the last 48 hours of the error.log the server became unresponsive during this period...But, I can't figure out where.  I am in the process of sun-setting a virtual dedicated server with Go-Daddy to this dedicated server, the SSL is split currently between the two servers which is where I think the RSA error is coming from.  I most certainly could be wrong, but everything I have read leads me to believe this isn't actually causing the issue with Apache.  Thoughts?
```

[Wed Dec 24 15:35:33.255837 2014] [ssl:warn] [pid 1991] AH01909: RSA certificate configured for roundcube.webmail:443 does NOT include an ID which matches the server name
[Wed Dec 24 15:35:33.268893 2014] [ssl:warn] [pid 1991] AH01909: RSA certificate configured for horde.webmail:443 does NOT include an ID which matches the server name
[Wed Dec 24 15:35:33.269155 2014] [ssl:warn] [pid 1991] AH01909: RSA certificate configured for lists:443 does NOT include an ID which matches the server name
[Wed Dec 24 15:35:33.269417 2014] [ssl:warn] [pid 1991] AH01909: RSA certificate configured for default-64_37_104_218:443 does NOT include an ID which matches the server name
[Wed Dec 24 15:35:33.269583 2014] [ssl:warn] [pid 1991] AH02292: Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)
[Wed Dec 24 15:35:33.269599 2014] [suexec:notice] [pid 1991] AH01232: suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec)
[Wed Dec 24 15:35:33.397790 2014] [auth_digest:notice] [pid 1999] AH01757: generating secret for digest authentication ...
[Wed Dec 24 15:35:33.634715 2014] [:notice] [pid 1999] mod_python: Creating 8 session mutexes based on 150 max processes and 0 max threads.
[Wed Dec 24 15:35:33.634736 2014] [:notice] [pid 1999] mod_python: using mutex_directory /tmp 
[Wed Dec 24 15:35:33.685588 2014] [ssl:warn] [pid 1999] AH01909: RSA certificate configured for roundcube.webmail:443 does NOT include an ID which matches the server name
[Wed Dec 24 15:35:33.685859 2014] [ssl:warn] [pid 1999] AH01909: RSA certificate configured for horde.webmail:443 does NOT include an ID which matches the server name
[Wed Dec 24 15:35:33.686121 2014] [sslwarn] [pid 1999] AH01909: RSA certificate configured for lists:443 does NOT include an ID which matches the server name
[Wed Dec 24 15:35:33.686398 2014] [ssl:warn] [pid 1999] AH01909: RSA certificate configured for default-64_37_104_218:443 does NOT include an ID which matches the server name
[Wed Dec 24 15:35:33.686568 2014] [ssl:warn] [pid 1999] AH02292: Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)
[Wed Dec 24 15:35:33.690211 2014] [mpm_prefork:notice] [pid 1999] AH00163: Apache/2.4.7 (Ubuntu) mod_fcgid/2.3.9 mod_python/3.3.1 Python/2.7.6 OpenSSL/1.0.1f mod_perl/2.0.8 Perl/v5.18.2 configured -- resuming normal operations
[Wed Dec 24 15:35:33.690239 2014] [core:notice] [pid 1999] AH00094: Command line: '/usr/sbin/apache2'
[Thu Dec 25 18:03:37.943546 2014] [ssl:warn] [pid 1951] AH01909: RSA certificate configured for roundcube.webmail:443 does NOT include an ID which matches the server name
[Thu Dec 25 18:03:37.956579 2014] [ssl:warn] [pid 1951] AH01909: RSA certificate configured for horde.webmail:443 does NOT include an ID which matches the server name
[Thu Dec 25 18:03:37.956840 2014] [ssl:warn] [pid 1951] AH01909: RSA certificate configured for lists:443 does NOT include an ID which matches the server name
[Thu Dec 25 18:03:37.957102 2014] [ssl:warn] [pid 1951] AH01909: RSA certificate configured for default-64_37_104_218:443 does NOT include an ID which matches the server name
[Thu Dec 25 18:03:37.957270 2014] [ssl:warn] [pid 1951] AH02292: Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)
[Thu Dec 25 18:03:37.957286 2014] [suexec:notice] [pid 1951] AH01232: suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec)
[Thu Dec 25 18:03:38.084434 2014] [auth_digest:notice] [pid 2000] AH01757: generating secret for digest authentication ...
[Thu Dec 25 18:03:38.327687 2014] [:notice] [pid 2000] mod_python: Creating 8 session mutexes based on 150 max processes and 0 max threads.
[Thu Dec 25 18:03:38.327709 2014] [:notice] [pid 2000] mod_python: using mutex_directory /tmp 
[Thu Dec 25 18:03:38.378722 2014] [ssl:warn] [pid 2000] AH01909: RSA certificate configured for roundcube.webmail:443 does NOT include an ID which matches the server name
[Thu Dec 25 18:03:38.379007 2014] [ssl:warn] [pid 2000] AH01909: RSA certificate configured for horde.webmail:443 does NOT include an ID which matches the server name
[Thu Dec 25 18:03:38.379273 2014] [ssl:warn] [pid 2000] AH01909: RSA certificate configured for lists:443 does NOT include an ID which matches the server name
[Thu Dec 25 18:03:38.379540 2014] [ssl:warn] [pid 2000] AH01909: RSA certificate configured for default-64_37_104_218:443 does NOT include an ID which matches the server name
[Thu Dec 25 18:03:38.379704 2014] [ssl:warn] [pid 2000] AH02292: Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)
[Thu Dec 25 18:03:38.383556 2014] [mpm_prefork:notice] [pid 2000] AH00163: Apache/2.4.7 (Ubuntu) mod_fcgid/2.3.9 mod_python/3.3.1 Python/2.7.6 OpenSSL/1.0.1f mod_perl/2.0.8 Perl/v5.18.2 configured -- resuming normal operations
[Thu Dec 25 18:03:38.383586 2014] [core:notice] [pid 2000] AH00094: Command line: '/usr/sbin/apache2'
[Thu Dec 25 18:34:06.765094 2014] [mpm_prefork:notice] [pid 2000] AH00171: Graceful restart requested, doing restart
[Thu Dec 25 18:34:07.050993 2014] [auth_digest:notice] [pid 2000] AH01757: generating secret for digest authentication ...
[Thu Dec 25 18:34:07.095538 2014] [:notice] [pid 2000] mod_python: Creating 8 session mutexes based on 150 max processes and 0 max threads.
[Thu Dec 25 18:34:07.095564 2014] [:notice] [pid 2000] mod_python: using mutex_directory /tmp 
[Thu Dec 25 18:34:07.200442 2014] [ssl:warn] [pid 2000] AH01909: RSA certificate configured for roundcube.webmail:443 does NOT include an ID which matches the server name
[Thu Dec 25 18:34:07.200717 2014] [ssl:warn] [pid 2000] AH01909: RSA certificate configured for horde.webmail:443 does NOT include an ID which matches the server name
[Thu Dec 25 18:34:07.201011 2014] [ssl:warn] [pid 2000] AH01909: RSA certificate configured for lists:443 does NOT include an ID which matches the server name
[Thu Dec 25 18:34:07.201278 2014] [ssl:warn] [pid 2000] AH01909: RSA certificate configured for default-64_37_104_218:443 does NOT include an ID which matches the server name
[Thu Dec 25 18:34:07.201448 2014] [ssl:warn] [pid 2000] AH02292: Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)
[Thu Dec 25 18:34:07.201982 2014] [mpm_prefork:notice] [pid 2000] AH00163: Apache/2.4.7 (Ubuntu) mod_fcgid/2.3.9 mod_python/3.3.1 Python/2.7.6 OpenSSL/1.0.1f mod_perl/2.0.8 Perl/v5.18.2 configured -- resuming normal operations
[Thu Dec 25 18:34:07.201995 2014] [core:notice] [pid 2000] AH00094: Command line: '/usr/sbin/apache2'
[Thu Dec 25 18:47:55.781550 2014] [mpm_prefork:notice] [pid 2000] AH00169: caught SIGTERM, shutting down
[Thu Dec 25 18:47:57.155612 2014] [ssl:warn] [pid 9791] AH01909: RSA certificate configured for roundcube.webmail:443 does NOT include an ID which matches the server name
[Thu Dec 25 18:47:57.156049 2014] [ssl:warn] [pid 9791] AH01909: RSA certificate configured for horde.webmail:443 does NOT include an ID which matches the server name
[Thu Dec 25 18:47:57.156453 2014] [ssl:warn] [pid 9791] AH01909: RSA certificate configured for lists:443 does NOT include an ID which matches the server name
[Thu Dec 25 18:47:57.156859 2014] [ssl:warn] [pid 9791] AH01909: RSA certificate configured for default-64_37_104_218:443 does NOT include an ID which matches the server name
[Thu Dec 25 18:47:57.157097 2014] [ssl:warn] [pid 9791] AH02292: Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)
[Thu Dec 25 18:47:57.157117 2014] [suexec:notice] [pid 9791] AH01232: suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec)
[Thu Dec 25 18:47:57.297431 2014] [auth_digest:notice] [pid 9792] AH01757: generating secret for digest authentication ...
[Thu Dec 25 18:47:57.318223 2014] [:notice] [pid 9792] mod_python: Creating 8 session mutexes based on 150 max processes and 0 max threads.
[Thu Dec 25 18:47:57.318246 2014] [:notice] [pid 9792] mod_python: using mutex_directory /tmp 
[Thu Dec 25 18:47:57.386633 2014] [ssl:warn] [pid 9792] AH01909: RSA certificate configured for roundcube.webmail:443 does NOT include an ID which matches the server name
[Thu Dec 25 18:47:57.386899 2014] [ssl:warn] [pid 9792] AH01909: RSA certificate configured for horde.webmail:443 does NOT include an ID which matches the server name
[Thu Dec 25 18:47:57.387160 2014] [ssl:warn] [pid 9792] AH01909: RSA certificate configured for lists:443 does NOT include an ID which matches the server name
[Thu Dec 25 18:47:57.387423 2014] [ssl:warn] [pid 9792] AH01909: RSA certificate configured for default-64_37_104_218:443 does NOT include an ID which matches the server name
[Thu Dec 25 18:47:57.387582 2014] [ssl:warn] [pid 9792] AH02292: Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)
[Thu Dec 25 18:47:57.391410 2014] [mpm_prefork:notice] [pid 9792] AH00163: Apache/2.4.7 (Ubuntu) mod_fcgid/2.3.9 mod_python/3.3.1 Python/2.7.6 OpenSSL/1.0.1f mod_perl/2.0.8 Perl/v5.18.2 configured -- resuming normal operations
[Thu Dec 25 18:47:57.391438 2014] [core:notice] [pid 9792] AH00094: Command line: '/usr/sbin/apache2'
[Thu Dec 25 19:08:38.975195 2014] [mpm_prefork:notice] [pid 9792] AH00171: Graceful restart requested, doing restart
[Thu Dec 25 19:08:39.210816 2014] [auth_digest:notice] [pid 9792] AH01757: generating secret for digest authentication ...
[Thu Dec 25 19:08:39.233343 2014] [:notice] [pid 9792] mod_python: Creating 8 session mutexes based on 150 max processes and 0 max threads.
[Thu Dec 25 19:08:39.233369 2014] [:notice] [pid 9792] mod_python: using mutex_directory /tmp 
[Thu Dec 25 19:08:39.695226 2014] [ssl:warn] [pid 9792] AH01909: RSA certificate configured for roundcube.webmail:443 does NOT include an ID which matches the server name
[Thu Dec 25 19:08:39.702220 2014] [ssl:warn] [pid 9792] AH01909: RSA certificate configured for horde.webmail:443 does NOT include an ID which matches the server name
[Thu Dec 25 19:08:39.702663 2014] [ssl:warn] [pid 9792] AH01909: RSA certificate configured for lists:443 does NOT include an ID which matches the server name
[Thu Dec 25 19:08:39.703101 2014] [ssl:warn] [pid 9792] AH01909: RSA certificate configured for default-64_37_104_218:443 does NOT include an ID which matches the server name
[Thu Dec 25 19:08:39.703351 2014] [ssl:warn] [pid 9792] AH02292: Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)
[Thu Dec 25 19:08:39.704056 2014] [mpm_prefork:notice] [pid 9792] AH00163: Apache/2.4.7 (Ubuntu) mod_fcgid/2.3.9 mod_python/3.3.1 Python/2.7.6 OpenSSL/1.0.1f mod_perl/2.0.8 Perl/v5.18.2 configured -- resuming normal operations
[Thu Dec 25 19:08:39.704076 2014] [core:notice] [pid 9792] AH00094: Command line: '/usr/sbin/apache2'
[Thu Dec 25 19:08:56.837243 2014] [mpm_prefork:notice] [pid 9792] AH00169: caught SIGTERM, shutting down
[Thu Dec 25 19:08:58.194446 2014] [ssl:warn] [pid 12013] AH01909: RSA certificate configured for roundcube.webmail:443 does NOT include an ID which matches the server name
[Thu Dec 25 19:08:58.194707 2014] [ssl:warn] [pid 12013] AH01909: RSA certificate configured for horde.webmail:443 does NOT include an ID which matches the server name
[Thu Dec 25 19:08:58.194965 2014] [ssl:warn] [pid 12013] AH01909: RSA certificate configured for lists:443 does NOT include an ID which matches the server name
[Thu Dec 25 19:08:58.195225 2014] [ssl:warn] [pid 12013] AH01909: RSA certificate configured for default-64_37_104_218:443 does NOT include an ID which matches the server name
[Thu Dec 25 19:08:58.195379 2014] [ssl:warn] [pid 12013] AH02292: Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)
[Thu Dec 25 19:08:58.195392 2014] [suexec:notice] [pid 12013] AH01232: suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec)
[Thu Dec 25 19:08:58.331957 2014] [auth_digest:notice] [pid 12014] AH01757: generating secret for digest authentication ...
[Thu Dec 25 19:08:58.352535 2014] [:notice] [pid 12014] mod_python: Creating 8 session mutexes based on 150 max processes and 0 max threads.
[Thu Dec 25 19:08:58.352558 2014] [:notice] [pid 12014] mod_python: using mutex_directory /tmp 
[Thu Dec 25 19:08:58.435342 2014] [ssl:warn] [pid 12014] AH01909: RSA certificate configured for roundcube.webmail:443 does NOT include an ID which matches the server name
[Thu Dec 25 19:08:58.435610 2014] [ssl:warn] [pid 12014] AH01909: RSA certificate configured for horde.webmail:443 does NOT include an ID which matches the server name
[Thu Dec 25 19:08:58.435902 2014] [ssl:warn] [pid 12014] AH01909: RSA certificate configured for lists:443 does NOT include an ID which matches the server name
[Thu Dec 25 19:08:58.436168 2014] [ssl:warn] [pid 12014] AH01909: RSA certificate configured for default-64_37_104_218:443 does NOT include an ID which matches the server name
[Thu Dec 25 19:08:58.436327 2014] [ssl:warn] [pid 12014] AH02292: Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)
[Thu Dec 25 19:08:58.440101 2014] [mpm_prefork:notice] [pid 12014] AH00163: Apache/2.4.7 (Ubuntu) mod_fcgid/2.3.9 mod_python/3.3.1 Python/2.7.6 OpenSSL/1.0.1f mod_perl/2.0.8 Perl/v5.18.2 configured -- resuming normal operations
[Thu Dec 25 19:08:58.440129 2014] [core:notice] [pid 12014] AH00094: Command line: '/usr/sbin/apache2'
```

---

### Post by TheFu on 2014-12-26
I think apache is just a symptom of other, worse, issues on the machine.  Fix those first. Look for hardware and other issues in /var/log/*log  dmesg, syslog,  If ssh isn't working, it takes a lot to break that - A LOT.

Troubleshooting on all computers comes down to "simplify, test, check the logs, repeat."  Change 1 thing at a time starting with the most basic to prove that isn't an issue, then move to the next level.  Might take 15-50 levels to finally get your entire.

Apache really shouldn't die, ever.  Even with the mismatched cert shown above.   Looks like there is a mod_perl issue and a perl program crashing the system.  I suspect you'll need a perl guru to solve that.  We stopped using mod_perl about 8 yrs ago and switched to WSGI servers with a front-end load balancer for our perl stuff, sorry I can't really help even though I am a perl guy.  

The suexec stuff is just scary to me on a webserver. If needed, that is a really poor architecture.  I actually run perl programs as non-privileged users. Doesn't help you today, but perhaps in the future.

---

### Post by MAFoElffen on 2014-12-26
Fu- You are right. Apache is not crashing there. It's shutting down gracefully, after the system is asked to shut-down. Then restarting the service after it reboots.

Yes, I'm suspecting hardware faults. I'm seeing that it's receiving a SIG-TERM signal... I'm suspecting that if he looks in the system log, that he's going to see the same as a received hardware SIG-TERM signal... Unattended = I'm thinking an NMI fault. If it is server iron, he could check the hardware/server logs. If not, then if it has BIOS hardware flags on the temps and/or voltages. Most common on those on old iron are PSU faults or CPU overheat conditions. At least, those are my initial guesses from what  I see in those logs.

---


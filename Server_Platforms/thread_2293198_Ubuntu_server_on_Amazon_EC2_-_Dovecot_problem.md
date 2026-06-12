---
title: "Ubuntu server on Amazon EC2 - Dovecot problem"
date: 2015-09-03
forum: Server Platforms
---

### Post by shawnblanchette on 2015-09-03
I haven't ran a server for a while and when I did I never really had issues. I never encountered an issue like this before. I've been waiting for important emails and as it turns out my mail server is down.

I don't know what all this means or how to fix it. I am using ISPConfig 3 and this comes from the Mail Error Log.


```
Sep 1 14:57:30 ip-172-31-24-89 amavis[1644]: (01644-10) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586.
Sep 1 14:57:30 ip-172-31-24-89 amavis[1643]: (01643-08) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586.
Sep 1 15:19:03 ip-172-31-24-89 dovecot: master: Error: service(imap): fork() failed: Cannot allocate memory
Sep 1 15:19:03 ip-172-31-24-89 dovecot: master: Error: service(imap): command startup failed, throttling for 2 secs
Sep 1 15:19:04 ip-172-31-24-89 dovecot: imap-login: Error: read(imap) failed: Connection reset by peer
Sep 1 15:19:15 ip-172-31-24-89 dovecot: master: Error: service(imap-login): fork() failed: Cannot allocate memory
Sep 1 15:19:15 ip-172-31-24-89 dovecot: master: Error: service(imap-login): command startup failed, throttling for 2 secs
Sep 1 15:19:22 ip-172-31-24-89 dovecot: master: Error: service(pop3-login): fork() failed: Cannot allocate memory
Sep 1 15:19:22 ip-172-31-24-89 dovecot: master: Error: service(pop3-login): command startup failed, throttling for 2 secs
Sep 1 15:19:25 ip-172-31-24-89 dovecot: master: Error: service(pop3-login): fork() failed: Cannot allocate memory
Sep 1 15:19:25 ip-172-31-24-89 dovecot: master: Error: service(pop3-login): command startup failed, throttling for 4 secs
Sep 1 15:19:29 ip-172-31-24-89 dovecot: master: Error: service(pop3-login): fork() failed: Cannot allocate memory
Sep 1 15:19:29 ip-172-31-24-89 dovecot: master: Error: service(pop3-login): command startup failed, throttling for 8 secs
Sep 1 15:19:33 ip-172-31-24-89 dovecot: master: Error: service(imap-login): fork() failed: Cannot allocate memory
Sep 1 15:19:33 ip-172-31-24-89 dovecot: master: Error: service(imap-login): command startup failed, throttling for 4 secs
Sep 1 15:19:37 ip-172-31-24-89 dovecot: master: Error: service(pop3-login): fork() failed: Cannot allocate memory
Sep 1 15:19:37 ip-172-31-24-89 dovecot: master: Error: service(pop3-login): command startup failed, throttling for 16 secs
Sep 1 15:19:53 ip-172-31-24-89 dovecot: master: Error: service(pop3-login): fork() failed: Cannot allocate memory
Sep 1 15:19:54 ip-172-31-24-89 dovecot: master: Error: service(pop3-login): command startup failed, throttling for 32 secs
Sep 1 15:20:21 ip-172-31-24-89 dovecot: master: Error: service(imap-login): fork() failed: Cannot allocate memory
Sep 1 15:20:21 ip-172-31-24-89 dovecot: master: Error: service(imap-login): command startup failed, throttling for 8 secs
Sep 1 15:22:17 ip-172-31-24-89 dovecot: master: Error: service(pop3-login): fork() failed: Cannot allocate memory
Sep 1 15:22:17 ip-172-31-24-89 dovecot: master: Error: service(pop3-login): command startup failed, throttling for 60 secs
Sep 1 15:22:29 ip-172-31-24-89 dovecot: master: Error: service(imap-login): fork() failed: Cannot allocate memory
Sep 1 15:22:29 ip-172-31-24-89 dovecot: master: Error: service(imap-login): command startup failed, throttling for 16 secs
Sep 1 15:22:59 ip-172-31-24-89 dovecot: master: Error: service(imap-login): fork() failed: Cannot allocate memory
Sep 1 15:22:59 ip-172-31-24-89 dovecot: master: Error: service(imap-login): command startup failed, throttling for 32 secs
Sep 1 15:27:17 ip-172-31-24-89 dovecot: master: Error: service(pop3-login): fork() failed: Cannot allocate memory
Sep 1 15:27:17 ip-172-31-24-89 dovecot: master: Error: service(pop3-login): command startup failed, throttling for 60 secs
Sep 1 15:31:31 ip-172-31-24-89 amavis[1643]: (01643-09) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586.
Sep 1 16:25:58 ip-172-31-24-89 amavis[1644]: (01644-11) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586, <GEN31> line 1162.
Sep 1 18:01:31 ip-172-31-24-89 amavis[1643]: (01643-10) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586, <GEN31> line 1391.
Sep 1 18:22:18 ip-172-31-24-89 dovecot: master: Error: service(pop3-login): fork() failed: Cannot allocate memory
Sep 1 18:22:18 ip-172-31-24-89 dovecot: master: Error: service(pop3-login): command startup failed, throttling for 2 secs
Sep 1 18:22:41 ip-172-31-24-89 postfix/smtp[9123]: fatal: load_library_symbols: dlopen failure loading /usr/lib/postfix/dict_mysql.so: libmysqlclient.so.18: failed to map segment from shared object: Cannot allocate memory
Sep 1 18:24:35 ip-172-31-24-89 dovecot: master: Error: service(imap-login): fork() failed: Cannot allocate memory
Sep 1 18:24:35 ip-172-31-24-89 dovecot: master: Error: service(imap-login): command startup failed, throttling for 2 secs
Sep 1 18:27:26 ip-172-31-24-89 dovecot: master: Error: service(pop3-login): fork() failed: Cannot allocate memory
Sep 1 18:27:27 ip-172-31-24-89 dovecot: master: Error: service(pop3-login): command startup failed, throttling for 4 secs
Sep 1 18:27:51 ip-172-31-24-89 dovecot: master: Error: service(pop3-login): fork() failed: Cannot allocate memory
Sep 1 18:28:06 ip-172-31-24-89 dovecot: master: Error: service(pop3-login): command startup failed, throttling for 8 secs
Sep 1 18:28:50 ip-172-31-24-89 dovecot: master: Error: service(pop3-login): fork() failed: Cannot allocate memory
Sep 1 18:29:04 ip-172-31-24-89 dovecot: master: Error: service(pop3-login): command startup failed, throttling for 16 secs
Sep 1 22:51:29 ip-172-31-24-89 amavis[1951]: (01951-02) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586.
Sep 1 22:55:41 ip-172-31-24-89 amavis[1952]: (01952-03) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586.
Sep 1 22:59:17 ip-172-31-24-89 amavis[1951]: (01951-03) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586, <GEN31> line 2545.
Sep 1 22:59:21 ip-172-31-24-89 amavis[1952]: (01952-04) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586, <GEN31> line 278.
Sep 1 22:59:21 ip-172-31-24-89 amavis[1951]: (01951-04) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586.
Sep 1 23:00:13 ip-172-31-24-89 amavis[1951]: (01951-05) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586, <GEN31> line 2716.
Sep 1 23:00:13 ip-172-31-24-89 amavis[1952]: (01952-05) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586, <GEN31> line 439.
Sep 1 23:00:42 ip-172-31-24-89 amavis[1951]: (01951-06) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586, <GEN31> line 3025.
Sep 1 23:01:49 ip-172-31-24-89 amavis[1952]: (01952-06) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586, <GEN31> line 550.
Sep 1 23:01:49 ip-172-31-24-89 amavis[1951]: (01951-07) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586, <GEN31> line 3150.
Sep 1 23:01:49 ip-172-31-24-89 amavis[1952]: (01952-07) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586.
Sep 1 23:03:26 ip-172-31-24-89 amavis[1952]: (01952-08) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586, <GEN31> line 697.
Sep 1 23:03:26 ip-172-31-24-89 amavis[1951]: (01951-08) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586, <GEN31> line 3284.
Sep 1 23:04:17 ip-172-31-24-89 amavis[1952]: (01952-09) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586, <GEN31> line 789.
Sep 1 23:04:17 ip-172-31-24-89 amavis[1951]: (01951-09) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586, <GEN31> line 3418.
Sep 1 23:04:17 ip-172-31-24-89 amavis[1952]: (01952-10) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586.
Sep 1 23:08:26 ip-172-31-24-89 amavis[1952]: (01952-11) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586, <GEN31> line 936.
Sep 1 23:08:26 ip-172-31-24-89 amavis[1951]: (01951-10) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586, <GEN31> line 3552.
Sep 1 23:08:26 ip-172-31-24-89 amavis[1952]: (01952-12) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586.
Sep 1 23:13:19 ip-172-31-24-89 amavis[1951]: (01951-11) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586.
Sep 2 06:15:08 ip-172-31-24-89 amavis[1952]: (01952-13) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586.
Sep 2 06:20:26 ip-172-31-24-89 amavis[1951]: (01951-12) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586, <GEN31> line 4459.
Sep 2 06:20:26 ip-172-31-24-89 amavis[1952]: (01952-14) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586, <GEN31> line 1988.
Sep 2 06:21:15 ip-172-31-24-89 amavis[1951]: (01951-13) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586, <GEN31> line 5312.
Sep 2 09:35:47 ip-172-31-24-89 amavis[1952]: (01952-15) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586.
Sep 2 09:35:50 ip-172-31-24-89 amavis[1951]: (01951-14) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586.
Sep 2 09:35:50 ip-172-31-24-89 amavis[1952]: (01952-16) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586.
Sep 2 13:44:34 ip-172-31-24-89 amavis[1952]: (01952-17) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586.
Sep 2 13:44:35 ip-172-31-24-89 amavis[1951]: (01951-15) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586.
Sep 2 13:44:35 ip-172-31-24-89 amavis[1952]: (01952-18) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586.
Sep 2 13:44:35 ip-172-31-24-89 amavis[1951]: (01951-16) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586.
Sep 2 13:46:40 ip-172-31-24-89 amavis[1952]: (01952-19) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586.
Sep 2 13:46:40 ip-172-31-24-89 amavis[1951]: (01951-17) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586.
Sep 2 13:46:40 ip-172-31-24-89 amavis[1952]: (01952-20) (!!)file(1) utility (/usr/bin/file) FAILED: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3586.
```

---

### Post by nerdtron on 2015-09-04
From these errors have you tried to reboot? looks like the server is running out of resources.

---

### Post by shawnblanchette on 2015-09-04
I did end up rebooting. I have been keeping an eye on things and I don't see any issues with resources. It may be an Amazon server on their equipment, but yes there are the exact same limits as a normal server (and a few 'quirks'). It's Ubuntu 14.04. All that is running on the server is Bind, Apache2, MySQL. Mailman, Dovecot, and Squirrelmail. I have a few error pages (1kb - 1.5kb) and that's about it right now. It's a fresh install. I've been setting these things up for fun for years and never encountered the issues I have with the EC2 'instance'. I would really hate to run two servers, one just for mail. If I have to then I have to.

Thank you I appreciate every answer!

---

### Post by SeijiSensei on 2015-09-04
Even a server with 1GB of memory should be able to run that suite of software with no problems.  I use Linode, not AWS, though, so I don't know what kinds of limits those VMs have.

---


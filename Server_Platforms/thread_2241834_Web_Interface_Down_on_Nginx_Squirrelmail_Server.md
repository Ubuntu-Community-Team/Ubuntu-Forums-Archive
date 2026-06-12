---
title: "Web Interface Down on Nginx Squirrelmail Server"
date: 2014-08-28
forum: Server Platforms
---

### Post by lingpanda on 2014-08-28
Hello All,

Currently using Squirrelmail with Nginx. Followed the following tutorial [http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-nginx-bind-dovecot-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-nginx-bind-dovecot-ispconfig-3)

I was in the squirrel config and made some changes and noticed the web interface no longer worked. Reversed changes and no luck. I can still send and receive email from a Thunderbird client. Server services show

[TABLE]
[TR]
 [TD]Web-Server:[/TD]
 [TD]Online[/TD]
[/TR]
 [TR]
 [TD]FTP-Server:[/TD]
 [TD]Online[/TD]
[/TR]
 [TR]
 [TD]SMTP-Server:[/TD]
 [TD]Online[/TD]
[/TR]
 [TR]
 [TD]POP3-Server:[/TD]
 [TD]Online[/TD]
[/TR]
 [TR]
 [TD]IMAP-Server:[/TD]
 [TD]Online[/TD]
[/TR]
 [TR]
 [TD]DNS-Server:[/TD]
 [TD]Online[/TD]
[/TR]
 [TR]
 [TD]mySQL-Server:[/TD]
 [TD]Online
[/TD]
[/TR]
[/TABLE]

Yet no luck on using the URL for access. Receive standard HTTP 500 error. Where do I start to troubleshoot? Thanks.

---

### Post by lingpanda on 2014-08-28
Some additional details in nginx error log

```
[error] 2978#0: *267 FastCGI sent in stderr: "PHP message: PHP Parse error:  syntax error, unexpected T_CONSTANT_ENCAPSED_STRING in /etc/squirrelmail/config.php on line 30" while reading response header from upstream, client: 172.16.232.30, server: _, request: "GET /squirrelmail/src/login.php HTTP/1.1", upstream: "fastcgi://127.0.0.1:9000", host: "172.16.232.48:8081"

```


This is line 30 from my squirrelmail config file

```
$domain                 = 'rim(implode('', file('/etc/'.(file_exists('/etc/mailname')?'mail':'host').'name'))';
```

---

### Post by lingpanda on 2014-08-28
Fixed by just changing the domain to my actual domain. How do I mark the thread fixed or solved? Thanks.

---

### Post by cariboo on 2014-08-29
Go to thread tools at the top of the page, and select Mark this thread as solved.

---


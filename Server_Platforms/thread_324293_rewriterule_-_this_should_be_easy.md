---
title: "rewriterule - this should be easy"
date: 2006-12-23
forum: Server Platforms
---

### Post by etotman on 2006-12-23
Server: Apache/2.0.55 (Ubuntu) PHP/5.1.2 (Installed with the LAMP option)

I think I'm missing something obvious.  Any suggestions or ideas would be greatly appreciated.

My ultimate goal is to turn off the HTTP TRACE method in apache.  I couldn't get that to work so I'm just trying a simple rewriterule command in /etc/apache2/httpd.conf like this:

<IfModule mod_rewrite.c>
RewriteEngine on
RewriteLogLevel 3
RewriteLog "/var/log/apache2/rewrite.log"
RewriteRule ^/$ [http://www.ubuntu.com](http://www.ubuntu.com) [R]
</IfModule>

The rewrite.log file is created but nothing is ever written to it.  The other apache log files are fine, so apache has permission to write there.

- mod_rewrite is loaded
- proxy is loaded
- I modified /etc/apache2/sites-available/default to allowoverride all
- I tried adding the code to apache2.conf but that didn't work either
- I restarted apache multiple times
- This command DOES work: Redirect / [http://www.ubuntu.com](http://www.ubuntu.com)
- no .htaccess file
- ran sudo a2enmod rewrite

What am I missing?

---

### Post by tturrisi on 2006-12-23
RewriteEngine On 
RewriteCond %{REQUEST_METHOD} ^TRACE 
RewriteRule .* - [F]

see second article down on this page:
[http://www.apacheweek.com/issues/03-01-24](http://www.apacheweek.com/issues/03-01-24)

---

### Post by etotman on 2006-12-23
I tried that first, but it didn't work.  I checked the syntax many times to be sure that I got it right too.

---

### Post by etotman on 2006-12-23
Okay, progress.  Now the rewriterule command works in a .htaccess file (per-dir) but the same command does nothing in httpd.conf or apache2.conf.  What could cause that?

---

### Post by etotman on 2006-12-23
It wasn't working in httpd.conf because I was missing the following commands:

<virtualhost *>
...
</virtualhost>

---

### Post by tturrisi on 2006-12-23
> **etotman said:**
> It wasn't working in httpd.conf because I was missing the following commands:

<virtualhost *>
...
</virtualhost>

good to know that.

---


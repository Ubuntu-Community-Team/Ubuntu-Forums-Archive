---
title: "Rewrite problem with vhosts"
date: 2009-10-16
forum: Server Platforms
---

### Post by martien on 2009-10-16
Hello everyone. I have little problem configuring mod_rewrite.
I want to make virtual subdomains with mod_rewrite and for a big site.
Simply i want **<<<someuser>>>**.mydomain.com/**<<something>>** to be rewrited to mydomain.com/script.php?user=**<<<someuser>>>**&opts=**<<something>>**.
For this i made *.mydomain.com A **<<myip>>** dns record for mydomain.com
and a vhost like this:
```
<VirtualHost myip>
 ServerAdmin root@localhost
 ServerName mydomain.com
 ServerAlias www.mydomain.com
 DocumentRoot /home/someplace/public_html
 ErrorLog /place/to/error.log
 CustomLog /place/to/access.log common
<Directory /home/someplace/public_html>
 OPTIONS Indexes Includes ExecCGI FollowSymLinks
 AllowOverride All
</Directory>
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteCond %{HTTP_HOST} !^www\.mydomain.com
RewriteCond %{HTTP_HOST} ([^.]+)\.mydomain.com
RewriteRule ^(.*).mydomain.com/(.*)$ script.php?user=%1&opts=%2 [L]
</IfModule>
</VirtualHost>

```
When i try to open mydomain.com in the browser its ok (opens index.php in /home/someplace/public_html), but when i try to open someuser.mydomain.com it opens the default virtualhost on my server and someuser.mydomain.com/something gives 404 (because there is no /something in the default VirtualHost) => the rewrite does not work.
PS. i have enabled mod_rewrite in the Apache configuration and it works with some other sites on my server.
Any ideas how to make that work?

---

### Post by t3r0 on 2009-10-17
Hi

The problem is that the virtualhost doesn't match the server name/server alias so the default site is displayed.

Change the ServerAlias to *.domain.com to solve this.

- Tero

---

### Post by martien on 2009-10-17
> **t3r0 said:**
> Hi

The problem is that the virtualhost doesn't match the server name/server alias so the default site is displayed.

Change the ServerAlias to *.domain.com to solve this.

- Tero
Thank you for the answer. I'm afraid that aint work. When i change ServerAlias to *.mydomain.com everything is pointed to mydomain.com without the rewrite... For some reason the rewrite rules doesnt work..
Any ideas?

---


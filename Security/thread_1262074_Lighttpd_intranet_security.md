---
title: "Lighttpd intranet security?"
date: 2009-09-09
forum: Security
---

### Post by Vunutus on 2009-09-09
I'm attempting to configure a Lighttpd intranet server for my small office. What I essentially want to do is allow anybody on the local network (192.168.1.*) to connect without being prompted for a password or anything, but just in case anyone wants to connect from a remote location, I would like to force users to authenticate using the username and password they already have on the server before any pages are shown to them.

If there is an easy way to do this I would appreciate if someone could tell me. If it's rather involved than I would appreciate a link/guide/whatever so I can read through myself.

---

### Post by bodhi.zazen on 2009-09-09
I am not sure you can do this from lighttpd alone, I suggest you configure OpenVPN.

---

### Post by Vunutus on 2009-09-09
> **bodhi.zazen said:**
> I am not sure you can do this from lighttpd alone, I suggest you configure OpenVPN.

Well it's a small business and I don't want to set up anything that complex just for this (since 99% of all connections will physically originate in the office).

Another question: Does Apache support this sort of thing?

---

### Post by bodhi.zazen on 2009-09-09
Yes I believe you can do this with apache, this is a snipit, you will have to test it =)

```
Order deny,allow[FONT=monospace]
[/FONT]Deny from all[FONT=monospace]
[/FONT]AuthName "Password Please"[FONT=monospace]
[/FONT]AuthUserFile /etc/apache2/access/.htpasswd[FONT=monospace]
[/FONT]AuthType Basic[FONT=monospace]
[/FONT]Require valid-user[FONT=monospace]
[/FONT]Allow from 192.168.1.0/16[FONT=monospace]
[/FONT]Satisfy Any
```

Put that in your site, under /etc/apache2/sites-available/your_site

Like this :

```
<VirtualHost *:80>
        ServerAdmin you@your_email.com
        ServerName  your_site.com
        DocumentRoot /var/www/your_site_home/
        <Directory /var/www/your_site_home>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order deny,allow
                Deny from all
                AuthName "htaccess password prompt"
                AuthUserFile /home/askapache.com/.htpasswd 
                AuthType Basic
                Require valid-user
                Allow from 192.168.1.0/16
                Satisfy Any
       </Directory>
```

---


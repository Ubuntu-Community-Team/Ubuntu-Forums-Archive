---
title: "Help with Squirrelmail/Apache"
date: 2011-02-14
forum: Server Platforms
---

### Post by NetworkSlacker on 2011-02-14
Hello and I do apologize if this is the wrong place or if this issue has been posted before however I am down to my wits end here. I cannot see squrrielmail from the internet nor can I get to the apache default web page and I have run out of options. I have followed the steps [here]("http://flurdy.com/docs/postfix/") to set up a working mail server and it can indeed send and receive mails however I cannot access the squirrelmail from the internet. Can anyone help me with this?

---

### Post by volkswagner on 2011-02-14
What does your /etc/apache2/sites-available/squirrelmail look like?

Do you get any errors in /var/log/apache2/error.log?

Do a firewall blocking port 80, or do you have any other functioning sites on Apache2 working outside your LAN?

Do you have proper DNS set for the domain name you are using for 
```
ServerName webmail.example.com
```

---

### Post by NetworkSlacker on 2011-02-14
Thanks for your reply. Here is the /etc/apache2/sites-available/squirrelmail

```

<Directory /usr/share/squirrelmail>
  Options FollowSymLinks
  <IfModule mod_php5.c>
    php_flag register_globals off
  </IfModule>
  <IfModule mod_dir.c>
    DirectoryIndex index.php
  </IfModule>

  # access to configtest is limited by default to prevent information leak
  <Files configtest.php>
    order deny,allow
    deny from all
    allow from 127.0.0.1
  </Files>
</Directory>

  #  users will prefer a simple URL like http://webmail.example.com
  <VirtualHost mywanip>
    DocumentRoot /usr/share/squirrelmail
    ServerName myhostname
  </VirtualHost>

# redirect to https when available (thanks omen@descolada.dartmouth.edu)
#
#  Note: There are multiple ways to do this, and which one is suitable for
#  your site's configuration depends. Consult the apache documentation if
#  you're unsure, as this example might not work everywhere.
#
#<IfModule mod_rewrite.c>
#  <IfModule mod_ssl.c>
#    <Location /squirrelmail>
#      RewriteEngine on
#      RewriteCond %{HTTPS} !^on$ [NC]
#      RewriteRule . https://%{HTTP_HOST}%{REQUEST_URI}  [L]
#    </Location>
#  </IfModule>
#</IfModule>

```Does this look correct to you?

---

### Post by NetworkSlacker on 2011-02-14
Here is the error log


```

[Sun Feb 13 08:04:34 2011] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.3 with Suhosin-Patch configured -- resuming normal operations
[Sun Feb 13 09:30:21 2011] [error] [client 24.185.147.225] Invalid method in request F\xc5\x1c\\[\x14\xc2y\x14\xba#\xc7\xde\xfa\xf2
[Sun Feb 13 09:31:52 2011] [error] [client 66.249.72.88] File does not exist: /var/www/robots.txt
[Sun Feb 13 11:30:46 2011] [error] [client 174.58.231.230] Invalid method in request tR\x80\xc2o\x91#\xea[
[Sun Feb 13 13:31:21 2011] [error] [client 174.48.56.213] request failed: error reading the headers
[Sun Feb 13 15:15:45 2011] [error] [client 58.218.204.110] script '/var/www/proxyheader.php' not found or unable to stat
[Sun Feb 13 18:03:24 2011] [error] [client 10.1.10.168] File does not exist: /var/www/favicon.ico
[Sun Feb 13 18:55:20 2011] [error] [client 202.129.207.198] client sent HTTP/1.1 request without hostname (see RFC2616 section 14.23): /w00tw00t.at.ISC.SANS.DFind:)
[Mon Feb 14 04:33:32 2011] [error] [client 109.230.251.9] script not found or unable to stat: /usr/lib/cgi-bin/textenv.pl
[Mon Feb 14 07:44:17 2011] [error] [client 58.218.204.110] script '/var/www/judge.php' not found or unable to stat
[Mon Feb 14 08:08:43 2011] [error] [client 58.218.204.110] script '/var/www/proxy-1.php' not found or unable to stat
[Mon Feb 14 13:56:34 2011] [notice] caught SIGTERM, shutting down
[Mon Feb 14 13:56:35 2011] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.3 with Suhosin-Patch configured -- resuming normal operations
[Mon Feb 14 13:57:19 2011] [notice] caught SIGTERM, shutting down
[Mon Feb 14 13:57:20 2011] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.3 with Suhosin-Patch configured -- resuming normal operations
[Mon Feb 14 14:00:27 2011] [notice] caught SIGTERM, shutting down
[Mon Feb 14 14:00:28 2011] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.3 with Suhosin-Patch configured -- resuming normal operations
[Mon Feb 14 15:22:06 2011] [error] [client 174.54.22.189] Invalid URI in request \xb3K\xb1\xf3\x86\vZ

```

Also, yes Port 80 is open and I am using Shorewall(as per the tutorial I used), which is something I am not familiar with. I think it might be the Shorewall configuration but I am not entirely sure, a shorewall check returns no errors.

---

### Post by volkswagner on 2011-02-14
> **NetworkSlacker said:**
>  

Does this look correct to you?

ServerName is f9networks owned by you?  Are you masking the actual content?  

Do you own a domain name?

Port 80 is not blocked as I can see your edited default web page... Kinda funny wizard!

---

### Post by NetworkSlacker on 2011-02-14
Sorry for the long delay. Yes f9networks is owned by me and I had forgot to mask the actual content in my haste to post. 
If you are seeing my wizard message then it means it is working and I cannot get out from any other machine here. I will have a friend try to access my site/squirrel mail in a few. Thanks for your reply again.

---

### Post by NetworkSlacker on 2011-02-14
I just tested through a proxy and roundcube works fine. Squirrelmail is 404'ed but that is a different issue I believe from me messing around from settings. It seems that I have an internal routing problem. volkswagner, thank you for your support, I would have driven my self crazy else-wise. 
I will mark this thread as solved.

---


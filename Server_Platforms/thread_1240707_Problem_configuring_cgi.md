---
title: "Problem configuring cgi"
date: 2009-08-15
forum: Server Platforms
---

### Post by jjalan on 2009-08-15
Hello,

I am a new user of Apache HTTP server and one of the thing I am trying  to do is to map all my request, valid or invalid in a way that a single script, say X (without any extension),  gets executed. For this I try to set my Document Root directory to my root directory, say www. I also the DirectryIndex to map to the script X.

DocumentRoot "/usr/local/apache2/www"

<Directory />
    Options FollowSymLinks +ExecCGI
    AllowOverride None
    Order deny,allow
    Deny from all
</Directory>

<Directory "/usr/local/apache2/www">
    AllowOverride None
    Options ExecCGI FollowSymLinks Indexes
    SetHandler cgi-script
    Order allow,deny
    Allow from all
</Directory>

Alias / "/usr/local/apache2/www/"

The above shows the relevant part of my httpd.conf file. I am working with latest version of Apache Server and Ubuntu 9.04. The problem I am facing is:

[1] Whenever I hit [http://localhost/](http://localhost/) , it always gives me 403 Error. In the error log, it tells me that I am trying to run directory as Script. I can however, run all the scripts beneath this folder (as desired).
[2] I am still not able to map all request to my localhost to this script. If I send an invalid request, it gives me URL not found error.

I was wondering if somebody could point me how to solve this problem. I also try using ScriptAlias instead of Alias but ended without any success.

-- 
Thanks,
Jaikishan

---


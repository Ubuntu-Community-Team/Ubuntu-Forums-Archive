---
title: "Apache showing text of CGI script rather than running CGI script"
date: 2017-05-17
forum: Server Platforms
---

### Post by weaver-nc on 2017-05-17
I am using Ubuntu 16.04 with Apache2.

When I try to load a cgi url I am getting the code rather than executing the cgi.

I have loaded the cgi module and cgi.load is in both mods-available and mods-enabled.  They point to /usr/lib/apache2/modules/mod_cgi.so which is there.

I have the following in my apache2.conf file: (/var/www.html/bugzilla has my cgi scripts in it).

```
ScriptAlias /cgi-bin/ /var/www/html/bugzilla/
<Directory “/var/www/html/bugzilla/”>
   AddHandler cgi-script .cgi .pl
   Options +ExecCGI
</Directory>

```

The only thing i the log file that even looks remotely odd is:
```
[Wed May 17 16:02:02.567484 2017] [mpm_prefork:notice] [pid 2802] AH00163: Apache/2.4.18 (Ubuntu) mod_perl/2.0.9 Perl/v5.22.1 configured -- resuming normal operations

```

When I run the index file via perl I get no errors:  "perl -T /var/www/html/bugzilla/index.cgi"

What am I missing?

---

### Post by waqt on 2017-05-22
Have you enabled CGI?

```
sudo a2enmod cgi
```

---

### Post by SeijiSensei on 2017-05-22
You might need to enable Indexes for /var/www/html/bugzilla/ or add "index.cgi" to the DirectoryIndex directive.  See [https://wiki.apache.org/httpd/DirectoryListings](https://wiki.apache.org/httpd/DirectoryListings).

---


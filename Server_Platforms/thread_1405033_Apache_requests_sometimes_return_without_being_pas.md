---
title: "Apache requests sometimes return without being passed through the php interpreter"
date: 2010-02-12
forum: Server Platforms
---

### Post by micdhack on 2010-02-12
Hello i am having a weird problem that i don't know how to debug.
After using sourceguardian on my website i can view it normally and all the pages are being printed without errors.
The problem is that sometimes instead of loading the webpages my browser prompts me to download the page. In that case the file index.php.
If i save the file on the disk it would be totally empty, 0 bytes.

The problem is that this occurrence happens about once or twice every 10 minutes.
I tried the commonlog and errorlog but nothing related there. The requests aren't even visible! I am not sure if this is a sourceguardian related problem or some other apache problem and i have no idea how to debug something that doesnt even register in the logs.

My apache configuration for this section is(i am connecting through vpn):

```
<VirtualHost 10.8.1.1>
    ServerName site.com
    DocumentRoot /var/www/site
    ServerAdmin urwebmaster@site.com
    ErrorLog /var/log/apache2/site-errorlog.log
    CustomLog /var/log/apache2/site-commonlog.log common
        ServerAlias www.site.com
        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        php_flag display_errors off
        php_flag log_errors on
        php_value error_log /var/www/site/PHP_errors.log
</VirtualHost>

```

---

### Post by wojox on 2010-02-12
[Try this]("https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205")

---

### Post by micdhack on 2010-02-12
I tried the above troubleshooting but everything was already enabled and ok.
In case that something would have been missing i would be getting the same error always. The thing is the website works normal but sometimes i get the download dialog.

---


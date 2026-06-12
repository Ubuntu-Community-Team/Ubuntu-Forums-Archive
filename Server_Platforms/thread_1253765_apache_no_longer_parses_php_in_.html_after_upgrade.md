---
title: "apache no longer parses php in .html after upgrade to jaunty"
date: 2009-08-30
forum: Server Platforms
---

### Post by maplon on 2009-08-30
Hi

I just upgraded to Jaunty. For some reason, the upgrade removed apache2 and php5. I reinstalled them.  The display of web pages and the parsing of PHP in .php files works fine.

But PHP no longer gets parsed in .html files. This worked before, with this setup:

In /etc/apache2/sites-available/default, I have:
```

       DocumentRoot /home/mpromber/public_html
        <Directory />
                Options FollowSymLinks
                AllowOverride All  
        </Directory>


```

and in /home/mpromber/public_html I have an .htaccess file with this line:

```
AddType application/x-httpd-php .html
```

AFAIK, the .htaccess file does get read by Apache: when I put gibberish on the first line I get a server error.

But PHP in files ending with .html  no longer gets parsed. This used to work, but I don't know whether I had any other module installed that I might need to get this to work. 

Any pointers?

---

### Post by maplon on 2009-08-30
Sorry! False alarm. PHP *was* getting parsed. It was a permission problem with images that were supposed to be displayed, and I got confused thinking they were handled by PHP.

---


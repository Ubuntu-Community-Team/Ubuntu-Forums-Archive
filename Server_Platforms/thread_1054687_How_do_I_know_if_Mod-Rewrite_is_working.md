---
title: "How do I know if Mod-Rewrite is working?"
date: 2009-01-29
forum: Server Platforms
---

### Post by Maheriano on 2009-01-29
I ran:
```
sudo a2enmod rewrite
```
and it was successful but when I go into Gallery2 on my website, it says it's not using mod-rewrite. Then I activate Permalinks in Wordpress and it breaks all the pages outside the main page.

---

### Post by conjur3r on 2009-01-30
Did you restart apache for the rewrite module to kick in?

---

### Post by Maheriano on 2009-01-30
> **conjur3r said:**
> Did you restart apache for the rewrite module to kick in?

Yes, restarted it. Then tried to reenable the module and it said it was already enabled. Then restarted Apache again. I cannot figure out why the regular Wordpress links work but as soon as I activate the Permalinks, all the pages break.

However on the website I have that's hosted remotely, which I pay for, Permalinks work perfectly fine. Must be a setting somewhere on my server, I figured it was with Rewrite.

---

### Post by cariboo on 2009-01-30
What does the apache error log say about your broken permalinks?

Jim

---

### Post by Zillion on 2009-01-30
If you create and upload a php file "phpinfo.php" with the following 
[PHP]
<?php
phpinfo();
?>
[/PHP]

When checking it with [www.yoursite.com/phpinfo.php](www.yoursite.com/phpinfo.php) check the section "apache", there should see mod_rewrite under loaded modules.

---

### Post by Maheriano on 2009-01-30
> **Zillion said:**
> If you create and upload a php file "phpinfo.php" with the following 
[PHP]
<?php
phpinfo();
?>
[/PHP]

When checking it with [www.yoursite.com/phpinfo.php](www.yoursite.com/phpinfo.php) check the section "apache", there should see mod_rewrite under loaded modules.

Yup. Does this mean it's working?

> Loaded Modules
core mod_log_config mod_logio prefork http_core mod_so mod_alias mod_auth_basic mod_authn_file mod_authz_default mod_authz_groupfile mod_authz_host mod_authz_user mod_autoindex mod_cgi mod_deflate mod_dir mod_env mod_mime mod_negotiation mod_php5 mod_rewrite mod_setenvif mod_status

---

### Post by Maheriano on 2009-01-30
> **cariboo907 said:**
> What does the apache error log say about your broken permalinks?

Jim

Where do I find this? Webmin? Under a certain folder?

EDIT - Found the location in webmin. Here's what the error.log says for the part where I was turning Permalinks on/off in Wordpress:
> [Thu Jan 29 20:44:51 2009] [error] [client 10.0.0.2] File does not exist: /home/deemar/public_html/examples/birth/about, referer: [http://10.0.0.6/examples/birth/](http://10.0.0.6/examples/birth/)
[Thu Jan 29 21:13:31 2009] [error] [client 10.0.0.2] File does not exist: /home/deemar/public_html/examples/birth/about, referer: [http://10.0.0.6/examples/birth/](http://10.0.0.6/examples/birth/)
[Thu Jan 29 21:25:26 2009] [error] [client 10.0.0.2] File does not exist: /home/deemar/public_html/examples/birth/wpg2, referer: [http://10.0.0.6/examples/birth/](http://10.0.0.6/examples/birth/)
[Thu Jan 29 21:25:56 2009] [error] [client 10.0.0.2] File does not exist: /home/deemar/public_html/examples/birth/wpg2, referer: [http://10.0.0.6/examples/birth/?page_id=3](http://10.0.0.6/examples/birth/?page_id=3)

I don't yet have it set up on a domain, just bought one yesterday and have to set up the name servers first. Using the IP for now. So it works when using the page_id but once I turn on Permalinks, it changes the URL to .../wpg2 or .../about and I assume Apache2 is looking for those folders which don't exist. They're just URL rewrites but it's still pointing to the same page as before.

---

### Post by conjur3r on 2009-01-30
> **Maheriano said:**
> 

Loaded Modules
core mod_log_config mod_logio prefork http_core mod_so mod_alias mod_auth_basic mod_authn_file mod_authz_default mod_authz_groupfile mod_authz_host mod_authz_user mod_autoindex mod_cgi mod_deflate mod_dir mod_env mod_mime mod_negotiation mod_php5 [COLOR=Red]**mod_rewrite**[/COLOR] mod_setenvif mod_status


Yeah it's on!

The other method to see if you have it available and when you do not have php installed is to run the following in a command line (it could be apache2ctl):

# sudo apachectl -t -D DUMP_MODULES

So now that you know the rewrite module is on, the next step is to configure your rewriting rules.  This can be done through httpd.conf or in .htaccess.  Most of the time, the web apps provide a htaccess file within the distribution but may have it disabled by renaming it.  You should follow their instructions on enabling pretty urls.

---

### Post by Maheriano on 2009-01-30
> **conjur3r said:**
> Yeah it's on!

The other method to see if you have it available and when you do not have php installed is to run the following in a command line (it could be apache2ctl):

# sudo apachectl -t -D DUMP_MODULES

So now that you know the rewrite module is on, the next step is to configure your rewriting rules.  This can be done through httpd.conf or in .htaccess.  Most of the time, the web apps provide a htaccess file within the distribution but may have it disabled by renaming it.  You should follow their instructions on enabling pretty urls.

Where do I find these 2 files and am I looking for an online guide on how to work them? I found both of them in various Apache2 folders but they were blank.

---

### Post by Zillion on 2009-01-31
You need to create a .htaccess file with some mod_rewrite rules in the root of your website, else rewrite function will not work good. 

Put this in it and save it as .htaccess :

```


# BEGIN WordPress
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [L]
</IfModule>

# END WordPress

```

---

### Post by Maheriano on 2009-01-31
> **Zillion said:**
> You need to create a .htaccess file with some mod_rewrite rules in the root of your website, else rewrite function will not work good. 

Put this in it and save it as .htaccess :

```


# BEGIN WordPress
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [L]
</IfModule>

# END WordPress

```

Does it matter if it's called rewrite.so and not mod_rewrite.c? Also, I have no idea what that stuff means, is there a place I can learn how to write a proper mod_rewrite or just copy a full one? The reason I ask is because that still didn't work, I put a .htaccess file with that information into my public_html folder, restarted Apache and activated Permalinks again in Wordpress. Page broken.

---

### Post by Maheriano on 2009-02-02
???

---

### Post by Maheriano on 2009-02-02
Got it. I followed another tutorial I found on this forum and did the following:

> deemar@Jurassic:/etc/bind$ sudo nano /etc/apache2/sites-enabled/deemarwebdesign


That opened a document which contained the following where I changed the ALLOWOVERRIDE from NONE to ALL.

>         <Directory /home/deemar/public_html>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride all
                Order allow,deny
                allow from all
        </Directory>


Then I restarted Apache2:

> sudo /etc/init.d/apache2 restart

It works!

---


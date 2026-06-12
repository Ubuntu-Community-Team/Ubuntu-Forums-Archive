---
title: "mediawiki apache2 problems"
date: 2013-02-10
forum: Server Platforms
---

### Post by fernandoch on 2013-02-10
Hello,

I installed mediawiki manually and it is working, this is the virtual host

```
<VirtualHost *:80>
     ServerAdmin webmaster@mysite.com
     ServerName mysite.com
     ServerAlias www.mysite.com
     Alias /wiki /srv/www/media/w
     DocumentRoot /srv/www/mysite.com/public_html/
     ErrorLog /var/log/apache2/mysite.com.error.log
     CustomLog /var/log/apache2/mysite.com.access.log combined
</VirtualHost>
```

Now I want to enable the short url to remove the index.php and I need to add some rewrites. These are the rewrites taken from here [http://www.mediawiki.org/wiki/Manual:Short_URL/Apache#Setting_up_the_rewrite_rules](http://www.mediawiki.org/wiki/Manual:Short_URL/Apache#Setting_up_the_rewrite_rules)

```
## http://www.mediawiki.org/wiki/Manual:Short_URL/Apache
 
# Enable the rewrite engine
RewriteEngine On 
# Short url for wiki pages
RewriteRule ^/?wiki(/.*)?$ %{DOCUMENT_ROOT}/w/index.php [L] 
# Redirect / to Main Page
RewriteRule ^/*$ %{DOCUMENT_ROOT}/w/index.php [L]
```

How should I add these? In a directory?

Thank you.

---

### Post by SeijiSensei on 2013-02-10
No, just add them to the definition of the <VirtualHost> that you have now.  Add them below the CustomLog directive.  Make sure to restart Apache after you do so with "sudo service apache2 restart".

---

### Post by fernandoch on 2013-02-10
It does not work. Maybe because it is an alias? In /srv/www/mysite.com/public_html/ I have a wordpress.

Any clues? Will I have to stick to the ugly index.php?

---

### Post by SeijiSensei on 2013-02-10
If the only index file is index.php, you can just end the URL at "/" and Apache will use index.php in the DocumentRoot.  If you want to get rid of all references to index.php, you'll have to play around with that rewrite rule.

Frankly I don't think it's ugly at all.  I've written quite a few sites where index.php is included in the URL when I need to pass parameters with a GET.  

In WordPress, you can control how a posting's URL appears in the composition window.  I use the /YYYY/MM/DD/title-of-the-posting/ style myself.  Just edit the "permalink" at the top of the composition window.  To set the default, go to Settings > Permalink in the Dashboard.

---

### Post by fernandoch on 2013-02-10
Thank you, but I would like to remove it from mediawiki.

---


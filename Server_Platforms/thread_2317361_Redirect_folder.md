---
title: "Redirect folder"
date: 2016-03-15
forum: Server Platforms
---

### Post by kambiz2 on 2016-03-15
Hi,
My internet provider has created a subdomain to our ubuntu server. I'd like to do a redirect, because the default page is apache's web.
Which is the best way to do it, modifiying apache2.conf or replacing the actual index.html with a perminent redirect to the folder I want.

Actualy, the default is /var/www/html/index.html and I'd like /www/www/html/owncloud/index.html

Thanks

---

### Post by nerdtron on 2016-03-16
Modify the apache2.conf and change the DocumentRoot directive on the configuration. Then restart the apache2 service.

---

### Post by kambiz2 on 2016-03-16
Thanks [COLOR=#000000]nerdtron, apache2.conf does not have DocumentRoot asigned. Instead of here I've found in /sites-availabe/000-default.conf

Another question:  what is better:
- change DocumentRoot or
- the subdomain links directly to the new folder?

Thanks again


[/COLOR]

---

### Post by wellsilva-email on 2016-03-16
Hi kambiz2,

Yeah, the default website and is  the 000-default.conf and changing the document root there will make your server deliver the webpage under this new document root. 

You mentioned subdomains. If you have "site.org" in your server and you want "wiki.site.org" as well, you will need to create new files inside sites-enabled.  You can find a detailed guide about this in [the Apache documentation]("https://httpd.apache.org/docs/current/vhosts/").

So, if you only need "site.org", you can go for changing the 000-default.conf. Simply because it's already there.

Hope to have helped, let us know if you need more information. Peace.

---

### Post by SeijiSensei on 2016-03-16
> **wellsilva-email said:**
> You mentioned subdomains. If you have "site.org" in your server and you want "wiki.site.org" as well, you will need to create new files inside sites-enabled.  You can find a detailed guide about this in [the Apache documentation]("https://httpd.apache.org/docs/current/vhosts/").
Not necessarily.  If wiki.site.org is an alias for site.org, then you can use the ServerAlias directive in the virtual host's configuration.

```

<VirtualHost *:80>
     ServerName    site.org
     ServerAlias   www.site.org wiki.site.org

     [etc.]
</VirtualHost>

```

However if you want to redirect all references for site1.example.com to site2.example.com, the easiest solution is to create a configuration file in /etc/apache2/sites-available/ like this:
```

<VirtualHost *:80>
     ServerName site1.example.com

     Redirect / http://site2.example.com
</VirtualHost>

```
Save this as a file like site1.conf in the /sites-available/directory then run
```
sudo a2ensite site1
```
That will "enable" the configuration by creating a symbolic link to the site1.conf file in /etc/apache2/sites-enabled/.

---

### Post by wellsilva-email on 2016-03-16
Yeah**, **[**[COLOR=#000000]SeijiSensei, [/COLOR]**[COLOR=#000000]agreed[/COLOR]]("http://ubuntuforums.org/member.php?u=698195").

He mentioned other document root in the same server, but talked about new subdomains and redirection, so I thrown the info in a way to see what he was up to.

In any case, with your info here he can do redirections if it's the case, let's see.

---


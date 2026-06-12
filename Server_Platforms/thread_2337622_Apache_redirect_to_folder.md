---
title: "Apache redirect to folder"
date: 2016-09-20
forum: Server Platforms
---

### Post by fernandoch on 2016-09-20
Hello,

How can I redirect all traffic to mydomain.com to mydomain.com/wiki with apache?

This is my virtualhost

```
<VirtualHost *:80>
     ServerAdmin webmaster@mydomain.com
     ServerName mydomain.com
     ServerAlias www.mydomain.com
     DocumentRoot /srv/www/mydomain.com/public_html/     
     ErrorLog /var/log/apache2/mydomain.com.error.log
     CustomLog /var/log/apache2/mydomain.com.access.log combined
</VirtualHost>
```

How to do it?

```
Redirect "/" "/wiki"
```

Does not work, it creates a loop.

Thanks

---

### Post by newbie-user on 2016-09-20
What about changing the DocumentRoot to point straight at the wiki directory?

---

### Post by fernandoch on 2016-09-20
This is another option, but mediawiki needs to be in the wiki folder.

Check this for more reasons why it is a bad idea

[https://www.mediawiki.org/wiki/Manual:Wiki_in_site_root_directory#Reasons_why_putting_wiki_pages_in_the_root_directory_of_the_web_site_is_bad](https://www.mediawiki.org/wiki/Manual:Wiki_in_site_root_directory#Reasons_why_putting_wiki_pages_in_the_root_directory_of_the_web_site_is_bad)

Also have a look at the wikipedia how they have the wiki folder too.

Anyone else for the redirect?

---

### Post by SeijiSensei on 2016-09-20
You need to use a complete URL like this:
```
Redirect / http://mydomain.com/wiki
```
Put this inside the <VirtualHost> container.

---

### Post by fernandoch on 2016-09-21
It does not work, I get this in the browser

[http://mydomain.com/wikiwikiwikiwikiwikiwikiwikiwikiwikiwikiwikiwikiwikiwikiwikiwikiwikiwikiwikiwikiwiki/](http://mydomain.com/wikiwikiwikiwikiwikiwikiwikiwikiwikiwikiwikiwikiwikiwikiwikiwikiwikiwikiwikiwikiwiki/)

---

### Post by SeijiSensei on 2016-09-21
Try putting a slash at the end of "/wiki" in the Redirect, i.e., "/wiki/".

Personally I'd just do what newbie-user suggests and make the wiki directory the DocumentRoot.  I didn't find that link you gave us very persuasive.

---

### Post by fernandoch on 2016-09-21
Now I get this

[http://mydomain.com/wiki/wiki/wiki/wiki/wiki/wiki/wiki/wiki/wiki/wiki/wiki/wiki/wiki/wiki/wiki/wiki/wiki/wiki/wiki/wiki/wiki/](http://mydomain.com/wiki/wiki/wiki/wiki/wiki/wiki/wiki/wiki/wiki/wiki/wiki/wiki/wiki/wiki/wiki/wiki/wiki/wiki/wiki/wiki/wiki/)

Don't you think wikipedia would have moved the DocumentRoot if it were a good idea?

Here is their main page

[https://en.wikipedia.org/wiki/Main_Page](https://en.wikipedia.org/wiki/Main_Page)

As a solution for now I am using this

RedirectMatch ^/$ /wiki

But could not find a way to make the Redirect work...

---

### Post by SeijiSensei on 2016-09-21
You could try a Rewrite rule, too.

```

RewriteEngine   On
RewriteRule     ^/$     /wiki [R]

```

Place this above any <Directory> stanzas.

The "[R]" tells Apache to reload the site after rewriting the URL.

---

### Post by newbie-user on 2016-09-22
From what I've been reading on mediawiki, the recommended setup is to have the /wiki as part of the URL. [They warn against shortening the URL]("https://www.mediawiki.org/wiki/Manual:Short_URL#Recommended_how-to_guide_.28setup_used_on_Wikipedia.29"). But they also provide some [direction on how to do short url]("https://www.mediawiki.org/wiki/Manual:Short_URL/Apache") in apache

---

### Post by fernandoch on 2016-09-23
Thanks a lot, will check it out :)

---


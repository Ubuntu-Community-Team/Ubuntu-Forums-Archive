---
title: "301 Redirect Advice"
date: 2010-04-28
forum: Server Platforms
---

### Post by ravingmad on 2010-04-28
Hi all, I'm hoping someone can help me with some advice on a particular apache 301 redirect scenario.

I have an existing web site running an ASP forum and I have migrated this to a Joomla CMS system which is working like a charm (still in test mode). The existing web site is a high ranking site and has almost 2000 pages indexed in Google so I have to set up 301 redirects to the new content on the Joomla site. That part I have no problem with as I found a working redirect (below) for that but my question is what kind of load will this place on the server having a large list of 2000 redirects? 

I've done much reading and the advice that seems most suitable so far is to put the redirects into the httpd.conf file for the site and not in the .htaccess file. From what I have read is that Apache loads the httpd.conf file only once whereas .htaccess gets hit and has to be read constantly. The redirect code I have now which works like a charm is the following:

RewriteEngine on
RewriteCond %{QUERY_STRING} ^TOPIC_ID=145$
RewriteRule .? [http://new.website.co.za/newurl.html/?](http://new.website.co.za/newurl.html/?) [R=301,L]
RewriteCond %{QUERY_STRING} ^TOPIC_ID=146$
RewriteRule .? [http://new.website.co.za/newurl2.html/?](http://new.website.co.za/newurl2.html/?) [R=301,L]

Does anyone foresee that this will be a problem having an httpd.conf file with over 4000 lines of redirects in it? 
Is there a better way to redirect than the above code?

Considering the Ubuntu server where this site will be running only has about 5 sites on it and they are all low usage sites, the server will be pretty much dedicated to this new Joomla version of the site and after a month or two I will remove all the redirects. 

Anyways, I look forward to any advice or suggestions.

Thanks in advance.

---

### Post by cdenley on 2010-04-28
It might be more efficient to do a single initial redirect like
```

RewriteCond %{QUERY_STRING} ^TOPIC_ID=.*$
RewriteRule ^/(.*)$ /redirect.php/$1 [R=301,L]

```

Then create the PHP script "redirect.php" to lookup mappings in a database you created using "$_SERVER['PATH_INFO']" then redirect to the appropriate page.

---

### Post by windependence on 2010-04-28
If you are running your Apache and new Joomla on any flavor of 'nix you should be fine. I run a forum with about 12,000 page views per day and the whole site is redirected like yours for the same reason. I have been running it like that for 2 years now with no performance issues at all. I'm using a redirect similar to what cdenley suggested. Server load is so low it's ridiculous, and this runs on a dual processor single core machine. 

-Tim

---

### Post by ravingmad on 2010-04-29
Thanks so much guys, really appreciate the feedback, much appreciated.

---


---
title: "Alternative to Apache .htaccess configuration"
date: 2019-03-01
forum: Server Platforms
---

### Post by Drone4four on 2019-03-01
I&#8217;ve got a basic Apache webserver running with 3 vhosts showcasing some content. I am not running any CMS software, just basic html and css. When a site viewer tries to navigate to a subfolder on my site (like /img/), I am trying to prevent  them from viewing its contents. Using .htaccess would do the trick, but official Apache docs advise against using .htaccess when necessary. 
 [Apparently]("https://httpd.apache.org/docs/2.4/howto/htaccess.html") &#8220;In general, you should only use .htaccess files when you don't have access to the main server configuration file.&#8221; In my case on my DigitalOcean VPS, I have access to all the configuration files. I should therefore use something else. But based on my reading of these docs, it&#8217;s not clear to me what my alternative is. The official  Apache docs continue:

> There is, for example, a common misconception that user authentication should always be done in .htaccess files, and, in more recent years, another misconception that mod_rewrite directives must go in .htaccess files. This is simply not the case. **You can put user authentication configurations in the main server configuration, and this is, in fact, the preferred way to do things. Likewise, mod_rewrite directives work better, in many respects, in the main server configuration.**

I'm confused. When the Apache doc refers to &#8220;main configuration&#8221;, are they referring to /etc/apache/sites-available/<site>.conf-le-ssl.conf? If so, what else should I include in my /etc/apache/sites-available/<site>.conf-le-ssl.conf to create the same effect that .htaccess would?

Or perhaps the better question for me to ask would be: What keywords should I search for on Google which would turn up the guide I need on how to create the same effect as .htaccess (redirecting site viewers who navigate to a subfolder on my site which would prevent them from viewing its contents)?

---

### Post by TheFu on 2019-03-01
If the file will be downloaded to the browser like any client-side js or content or CSS, then the clients will be able to read it.  If you just want to prevent a directory listing, don't include the index option in the apache config for that directory.
```

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options **Indexes** -MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 192.168.1.0/255.255.255.0 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

```
So, _in the options, remove the bold text._  Wouldn't hurt to place an empty index.html file there too ... "nothing to see here." But any of the files that must be used by the clients will be possible to see with a tiny bit of effort. You can force the referrer to from your website to make it a little harder. This is good for image files that you don't want being referenced by other sites. Why should you pay for their bandwidth?  I don't do that in apache. Mostly use nginx here.

[https://wiki.apache.org/httpd/DirectoryListings](https://wiki.apache.org/httpd/DirectoryListings) has more.

---


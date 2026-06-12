---
title: "virtual host file with ruby directory structure"
date: 2008-03-27
forum: Server Platforms
---

### Post by mickey13 on 2008-03-27
Hi all,

The problem I'm having right now is I'm not able to get my ruby app to work with my apache server.  I believe it's a problem with my virtual host file, as I can get the default rails page (public/index.html) to show up fine as the welcome page for my website.  Here's a snippet from my virtual host file:

<VirtualHost *>
    ServerName [www.example.com](www.example.com)
    ServerAlias example.com

    DocumentRoot /var/www/example.com/public

    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>

    <Directory /var/www/example.com/public/>
        Options Indexes FollowSymLinks Multiviews
        AllowOverride all
        Order allow,deny
        allow from all
    </Directory>

...

</VirtualHost>


How do I get apache to know about my view in app/views/wecome/index.html.erb  ?

Thanks in advance for the help!
Mickey

---


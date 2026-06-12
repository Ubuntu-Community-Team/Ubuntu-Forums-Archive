---
title: "apache2 is not reading .htaccess properly"
date: 2013-08-02
forum: Server Platforms
---

### Post by George_IsintheComputer on 2013-08-02
I just enabled htaccess on my site. It's now changing story.php?title= into /story/title
But when I clicked on the story link, I get 404 not found.

I have edited the 'default' file in /etc/apache2/sites-available/default and enabled AllowOverride and restarted.

[HTML]<Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
</Directory>[/HTML]

But that didn't solve the problem.

---


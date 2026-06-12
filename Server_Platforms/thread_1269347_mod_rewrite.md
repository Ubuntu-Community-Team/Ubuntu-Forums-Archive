---
title: "mod_rewrite"
date: 2009-09-18
forum: Server Platforms
---

### Post by richard.johansson on 2009-09-18
I am having problems with my Jaunty regarding setting up a mod_rewrite in order to function for the site that I just moved to the server. The rewrite module is enabled but I have not yet understood where that I am supposed to do the changes to the Apache configuration files in order to make it do the rewrite functionality in the way that I wish for it to do.

I have installed Jaunty Server (9.04) from scratch and the created two sites, one for the port 80 and one for port 443, as I couldn't find any simple documentation on how I did forward all requests for the HTTP site to the HTTPS site anywhere - anyone? 

Further on, I wonder if there is any good mod_rewrite tutorial that any one of you know about and can send me a tip about.

Any help appreciated!

---

### Post by terazen on 2009-09-18
This may not be what you are looking for, but the way I did it on my server was like this:```
        <Directory /var/www/virtual/mysite/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                RedirectPermanent / https://www.mysite.com/
                Order allow,deny
                allow from all
        </Directory>

```

When I was trying to redirect http to https it seemed there was a couple ways to do it and this was least complicated looking.  Just add RedirectPermanent to the /etc/apache2/sites-available/yoursite file for the http site and restart apache.

---

### Post by slakkie on 2009-09-18
> **richard.johansson said:**
> I am having problems with my Jaunty regarding setting up a mod_rewrite in order to function for the site that I just moved to the server. The rewrite module is enabled but I have not yet understood where that I am supposed to do the changes to the Apache configuration files in order to make it do the rewrite functionality in the way that I wish for it to do.

I have installed Jaunty Server (9.04) from scratch and the created two sites, one for the port 80 and one for port 443, as I couldn't find any simple documentation on how I did forward all requests for the HTTP site to the HTTPS site anywhere - anyone? 

Further on, I wonder if there is any good mod_rewrite tutorial that any one of you know about and can send me a tip about.

Any help appreciated!

```

<VirtualHost _default_:80>
    ServerName myserver.opperschaap.net
    RedirectMatch ^/(.*) https://myserver.opperschaap.net:443/$1
</VirtualHost>

# Your SSL site:
<VirtualHost _default_:443>
DocumentRoot "/opt/apache/htdocs"
ServerName myserver.opperschaap.net
# More stuff here... 
</VirtualHost>

```

---

### Post by openfly on 2009-09-18
mod_rewrite commands are usually setup inside of the <Directory> stuff as seen above.  But be careful of virtual hosts, as well as SSL.

There's <Directory> flags in all three sets of locations.

---


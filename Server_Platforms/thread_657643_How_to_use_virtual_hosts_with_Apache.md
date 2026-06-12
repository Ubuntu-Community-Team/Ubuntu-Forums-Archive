---
title: "How to use virtual hosts with Apache?"
date: 2008-01-03
forum: Server Platforms
---

### Post by Scooter7 on 2008-01-03
Hi,

I'm using Apache2 on an Ubuntu 7.04 server.   I want to have [www.team-sanity.net](www.team-sanity.net) pointing at /var/www/team_sanity1 on my server.   Currently the domain points to /var/www/index.html, so I'm trying to use virtual hosts to do this, but I'm completely new to using domain names or virtual hosts.

So far I've created a file called team-sanity in /etc/apache2/sites-available:

> NameVirtualHost *
<VirtualHost *>
        ServerAdmin [email]vertimyst@gmail.com[/email]

        ServerName [www.team-sanity.net](www.team-sanity.net)

        DocumentRoot /var/www/team_sanity1/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

And created a symlink to it and the file in /etc/apache2/sites-enabled, as well as edited /etc/hosts to include the virtual host.   After restarting my server, however, the domain still points to the index.html file at /var/www/.   Note that this isn't for local development, as most virtual host guides seem to assume - I simply need a way for my domain to point to /var/www/team_sanity1/ instead of /var/www/.   My domain is registered with GoDaddy.com.   If anyone knows a better way to do this without virtual hosts, that would be great.

---

### Post by scxtt on 2008-01-03
i see 2 potential problems ...

1. i think you want the "team-sanity" defn. in sites-enabled
2. i think you should make your "team-sanity" in sites-available, then use a2ensite to make it "available" ...

what i did to get it working was just put my virtual_hosts defns in "default" ...

also, if you have no use for /var/www - you can probably just point "default" to /var/www/team_sanity1 ... since default (/var/www) is just a virtual_host itself ...

---

### Post by Scooter7 on 2008-01-03
Thanks for the quick reply,

And "team-sanity" is already in sites-enabled, via a2ensite - that's what was meant when I said I "created a symlink to it and the file in /etc/apache2/sites-enabled".

Even so, I tried using a2ensite again, and it said it was already enabled.

---

### Post by scxtt on 2008-01-03
have you tried changing **/var/www** in "default" to **/var/www/team_sanity1**?

---

### Post by Scooter7 on 2008-01-03
Thanks, that did it.   I thought default was just a template, though.

---

### Post by scxtt on 2008-01-03
no, it's what makes /var/www work ... and it's an example of how to set up virtual hosts ... i wouldn't say i understand it 100%, but i was able to get 2 more virtual hosts going (1 for phpmyadmin and 1 for ampache) ... they do only work "locally", so i can't use my dyndns.org DNS name w/ them, but that's ok ...

---

### Post by Scooter7 on 2008-01-03
Ah, okay.   Changing the DocumentRoot in default did indeed allow the domain to work, but now anything pointing to my server, such as my DynDNS name ([http://shadowserve.ath.cx](http://shadowserve.ath.cx)), my IP, anything, points to the site.   I host multiple sites, normally accessed via [http://shadowserve.ath.cx/site-name/](http://shadowserve.ath.cx/site-name/), and they've all used freedomain.co.nr up to this point.   What I need is for [http://www.team-sanity.net](http://www.team-sanity.net) to point to [http://my-ip/team_sanity1/](http://my-ip/team_sanity1/) (or [http://shadowserve.ath.cx/team_sanity1/](http://shadowserve.ath.cx/team_sanity1/)).   Would you know how to go about doing this?

---

### Post by scxtt on 2008-01-03
i'm not sure how you'd get:

[http://www.team-sanity.net](http://www.team-sanity.net) --> [http://shadowserve.ath.cx/team_sanity1/](http://shadowserve.ath.cx/team_sanity1/)

since i've really only seen registered DNS names point to IP addresses, so

[http://DNS](http://DNS) --> [http://IP/folder](http://IP/folder)

doesn't make a lot of sense ...

the only thing i can think of would be 

point [http://www.team-sanity.net](http://www.team-sanity.net) --> [http://shadowserve.ath.cx/](http://shadowserve.ath.cx/)

test what the referring DNS name was and:

for [http://shadowserve.ath.cx/](http://shadowserve.ath.cx/)
if referring DNS = [http://www.team-sanity-A.net/](http://www.team-sanity-A.net/)
-- redirect to [http://shadowserve.ath.cx/team_sanity-A/](http://shadowserve.ath.cx/team_sanity-A/)
elseif referring DNS = [http://www.team-sanity-B.net/](http://www.team-sanity-B.net/)
-- redirect to [http://shadowserve.ath.cx/team_sanity-B/](http://shadowserve.ath.cx/team_sanity-B/)
else
-- redirect to [http://shadowserve.ath.cx/](http://shadowserve.ath.cx/)

---

### Post by Scooter7 on 2008-01-03
Well, using an IP in place of [http://shadowserve.ath.cx](http://shadowserve.ath.cx) is fine, it's just that I find it easier to remember.

Also, I should mention that I get this error when restarting Apache:

> apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Thu Jan 03 22:43:11 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Thu Jan 03 22:43:21 2008] [warn] NameVirtualHost *:0 has no VirtualHosts

---

### Post by scxtt on 2008-01-03
what do you have in /etc/hosts? you'll either need to define 127.0.0.1/127.0.1.1 better or set a hostname for your LAN IPs on that host ...

also -using PHP- i was able to get a page to redirect based on the referring site ... so it seems to me that you could have an index.php on [http://shadowserve.ath.cx/](http://shadowserve.ath.cx/) that tests to see if the user "came from" [http://www.team-sanity.net/](http://www.team-sanity.net/) ...

---

### Post by Scooter7 on 2008-01-03
> 127.0.0.1   localhost
127.0.0.1   shadowserve
127.0.0.1   team-sanity.net

is what I have in my /etc/hosts file.

---

### Post by scxtt on 2008-01-03
i'd use:

127.0.0.1 localhost
127.0.1.1 team-sanity.net shadowserve

---

### Post by Scooter7 on 2008-01-03
Alright, and what to use for the sites-available?   team-sanity is essentially a copy of default, with the values edited.   However, they haven't seemed to work.

---

### Post by scxtt on 2008-01-04
is [http://www.team-sanity.net/](http://www.team-sanity.net/) just forwarding to [http://shadowserve.ath.cx/](http://shadowserve.ath.cx/)?

i would forget about virtual hosts and just have EVERYTHING hit [http://shadowserve.ath.cx/](http://shadowserve.ath.cx/) then redirect depending on where the refer comes from ... i can show you the php code i have for it (it's pretty simple).

---

### Post by Scooter7 on 2008-01-04
Alright, I'll try the php.   Also, in my godaddy.com control panel I have a forward set up but it's not working for some reason.

---

### Post by scxtt on 2008-01-04
well, there's a snag w/ my php idea ... if you type [http://www.team-sanity.net/](http://www.team-sanity.net/) directly, HTTP_REFERER is "" (i.e. blank) so if someone were to type either [http://www.team-sanity.net/](http://www.team-sanity.net/) or [http://shadowserve.ath.cx/](http://shadowserve.ath.cx/), it would be "" in both cases, so that doesn't seem to be much help ... :|

so it almost seems that you'd just need a "gateway" page that would send people to the required content from either [http://www.team-sanity.net/](http://www.team-sanity.net/) or [http://shadowserve.ath.cx/](http://shadowserve.ath.cx/) -- not really all that graceful/

---

### Post by Scooter7 on 2008-01-04
Well, it's okay, because I've figured out how to use virtual hosts.

I had to put both shadowserve.ath.cx, pointing to /var/www/, and [www.team-sanity.net](www.team-sanity.net), pointing to /var/www/team_sanity1/ in the same vhosts file.   Then I did as you suggested and set my /etc/hosts file like this:

> 127.0.0.1   localhost
127.0.1.1   shadowserve [www.team-sanity.net](www.team-sanity.net)

Thanks for your help, though.   A few things you said helped me to figure this out.

---

### Post by scxtt on 2008-01-04
cool, good to hear :) ... i also learned a couple things too - since my use of vhosts has been very basic thus far ... i registered another DNS entry (i think i can get 5 for free) and set one of my vhosts to use it to forward to the phpmyadmin page - worked like a charm :) - how cool ...

---


---
title: "Trouble with apache virtual hosts"
date: 2007-04-26
forum: Server Platforms
---

### Post by Joespower on 2007-04-26
Hey all, I'm new at this so forgive me if my questions are obvious...

I'm trying to get an intranet going at work, and I'm having some issues.  What I want is to have two sites using named virtual hosts like so:
forums.dpgdomain.com
intranet.dpgdomain.com

I went ahead and made 2 A records on my DNS server, both of which point to 192.168.212.185 (should I have used CNAME records?).  Then, I made a copy of the default site in sites-available, renamed it to intranet and changed the necessary stuff, and then enabled it with a2ensite.  I did the same for forums, then I dissabled the default site with a2dissite.  Then, after I reload the server, what happens is that I get the forums website no matter which site I punch in, and if I dissable forums, only then will the intranet site work as expected.  I'm sure I'm overlooking something small here, but despite my trial and error I have yet to find it...

I'll post my 2 virtual host files here for further info.  I have a bunch of stuff commented out in both of them as a result of my trying to get stuff working.

NameVirtualHost 192.168.212.185

<VirtualHost 192.168.212.185>
        ServerName forums.dpgdomain.com
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/smf
#       <Directory />
#               Options FollowSymLinks
#               AllowOverride None
#       </Directory>
#       <Directory /var/www/>
#               Options Indexes FollowSymLinks MultiViews
#               AllowOverride None
#               Order allow,deny
#               allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
#       </Directory>

#       ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
#       <Directory "/usr/lib/cgi-bin">
#               AllowOverride None
#               Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
#               Order allow,deny
#               Allow from all
#       </Directory>

        ErrorLog /var/log/apache2/forums/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/forums/access.log combined
        ServerSignature On

#    Alias /doc/ "/usr/share/doc/"
#    <Directory "/usr/share/doc/">
#        Options Indexes MultiViews FollowSymLinks
#        AllowOverride None
#        Order deny,allow
 #        Deny from all
#        Allow from 127.0.0.0/255.0.0.0 ::1/128
#    </Directory>

</VirtualHost>


NameVirtualHost  192.168.212.185

<VirtualHost 192.168.212.185>
        ServerName intranet.dpgdomain.com
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/joomla
#       <Directory />
#               Options FollowSymLinks
#               AllowOverride None
#       </Directory>
#       <Directory /var/www/>
#               Options Indexes FollowSymLinks MultiViews
#               AllowOverride None
#               Order allow,deny
#               allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
#       </Directory>

#       ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
#       <Directory "/usr/lib/cgi-bin">
#               AllowOverride None
#               Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
#               Order allow,deny
#               Allow from all
#       </Directory>

        ErrorLog /var/log/apache2/intranet/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/intranet/access.log combined
        ServerSignature On

#    Alias /doc/ "/usr/share/doc/"
#    <Directory "/usr/share/doc/">
#        Options Indexes MultiViews FollowSymLinks
#        AllowOverride None
#        Order deny,allow
#               Options Indexes FollowSymLinks MultiViews
#               AllowOverride None
#               Order allow,deny
#               allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
#       </Directory>

</VirtualHost>

#<VirtualHost *>
#       ServerName forums.dpgdomain.com
#       ServerRoot /var/www/smf
#</VirtualHost>



Any ideas?

---

### Post by strixy on 2007-04-26
There are great examples on the apache doc site.

[http://httpd.apache.org/docs/2.2/vhosts/examples.html](http://httpd.apache.org/docs/2.2/vhosts/examples.html)

Just a couple of tips

Include a virtual domain path for your root domain eg. [www.domain.com](www.domain.com) as well as one for each of your sub.domains.com

Example adapted from [http://httpd.apache.org/docs/2.2/vhosts/name-based.html](http://httpd.apache.org/docs/2.2/vhosts/name-based.html)

```

 NameVirtualHost *:80

<VirtualHost *:80>
ServerName www.domain.tld
ServerAlias domain.tld www.domain.tld
DocumentRoot /var/www
</VirtualHost>

<VirtualHost *:80>
ServerName sub.domain.tld
DocumentRoot /var/www/sub
</VirtualHost>

```

---

### Post by Joespower on 2007-04-26
Thanks strixy.  I've read that before, but I wasn't sure it applied to my situation.  Now that I have tested it, I see that it works!  BUT, I have another question...

In my DNS server (which is Win2k AD DNS), I have 3 host records that point to this machine:

[www.dpgdomain.com](www.dpgdomain.com) -> intranet
intranet.dpgdomain.com -> intranet
forums.dpgdomain.com -> forums

The actual hostname of the machine is intranet, and all of these records point to 192.168.212.185.  When I type them in as above, I get what I expected, but if I just type the hostname, I always get the forums (eg. [http://intranet](http://intranet) -> forums).  Do I need to edit my hosts file somehow?  Is this because I'm using host records instead of CNAME records?  Am I just going to have to learn to always type the full FQDN if I want to get to the right place?

These forums rock!!

---

### Post by strixy on 2007-04-26
The thing I'm worried about isn't internal to your LAN, but your domain registrars handling of domain forwarding. Some offer domain forwarding, which basically opens a frame to a file and doesn't route the DNS at all. Some you can actually hand over your DNS services to a third party dynamic dns service (like zoneedit, dyndns, no-ip etc...). 

 NameVirtualHost *:80

<VirtualHost *:80>
ServerName dpgdomain.com
ServerAlias dpgdomain.com [www.dpgdomain.com](www.dpgdomain.com)
DocumentRoot /var/www
</VirtualHost>

<VirtualHost *:80>
ServerAlias intranet.dpgdomain.com
DocumentRoot /var/www/intranet
</VirtualHost>


<VirtualHost *:80>
ServerAlias forums.dpgdomain.com
DocumentRoot /var/www/smf
</VirtualHost>

---

### Post by Joespower on 2007-04-26
I'm not sure thats a problem, since this will only be accessed from inside my LAN.  This is strictly an intranet server, but we use different software for the different functions, such as joomla for portal (intranet) and simple machines forum for the forums.  I thought it would be nice to be able to access them directly, just like mail.google.com/maps.google.com or any of the other examples...

Is this what you were asking?

---


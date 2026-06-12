---
title: "Apache2 Named Virtual Host"
date: 2007-10-08
forum: Server Platforms
---

### Post by captnops on 2007-10-08
Can anyone point me to a step by step for creating and hosting virtual name based hosts.

I have STFA and every answer appear to be at odds with every other.

I have apache2.conf not httpd.conf
I have the /etc/apache2/sites-available/default.conf

My understanding of the steps is this:

1.  Add the NameVirtualHost * to the default file in sites-available
2. Add .conf files for each site to host.

I receive the following error when restarting apache:

NameVirtualHost *:0 has no VirtualHosts

Any help is greatly appreciated.  :confused:

---

### Post by ksudbury on 2007-10-08
Hi,

NameVirtualHost should appear only once and in your apache config file in /etc/apache2/apache2.conf

It should read: 

 # Listen for virtual host requests on all IP addresses
NameVirtualHost 10.0.0.103:80 
NameVirtualHost 10.0.0.103:443

(you only need 443 if you are using SSL)

10.0.0.103 should be replaced with your IP address.



# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/[^.#]*



The line above tells apache where to look for the vhost files. The vhost files you can call what you want AFAIK, for example yoursite.com 

they should look some thing like this:

NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
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
                RedirectMatch ^/$ /apache2-default/
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
  



Let me know how you get on.

Cheers

---

### Post by captnops on 2007-10-16
Thank you for the help.

Does the following line also appear in apache2.conf or in a different locaton?

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/[^.#]*

I have also heard others indicate that a seperate file should be created in the sites available folder w/symlink to sites available created in the sites enabled folder.  Is this still true?

Also some indicate that the Named Virtual host statement should be in either the httpd.conf file or as the first line line in the default doc in sites available?  Which is correct?

---

### Post by MJN on 2007-10-16
Just to add to what Keith's already said (all good stuff), the reason you're seeing some conflicting information is that the Apache on Debian-based distro's (Ubuntu included) has gone for a modular configuration on the basis that some Apache config files were getting vast and unwieldly. Hence, splitting the config out into functional compartments (e.g. main server config, site-specific config, etc) is intended to simplify matters, which it does when you're used to it, but it makes the initial document studying which make no mention of this Debian departure somewhat confusing!
 
Hence, you should now leave httpd.conf alone (it'll be all-but-empty but is kept (and parsed) in case any particular package expects it to exist) and use apache2.conf for your main server-related config. The config for your virtual hosts (which, if you've got more than site, covers *all* site - don't fall into the trap of thinking you've got a 'main' site and several 'virtual' ones... they're all virtual now (but you might have a 'default' one)) sits in /etc/apache2/sites-available/
 
The extra bit which you now need is to enable those sites (by including their config) using the a2ensite and a2dissite tools (run them with sudo and no arguments - it'll prompt you for which site you want enabling/disabling). All this does is put a symlink in sites-enabled/ to your config. You could do this manuall but I'd recommend getting used to using the higher-level tools as one day they will likely perform much more than simply adding/removing symlinks.
 
As Keith said you should only have one NameVirtualHost entry (per address: port) and I don't think it really matters where it goes - but don't put it in httpd.conf as that's out of bounds now if you're playing by the rules. Stick it in your default virtual host config file - it makes complete sense to have it there. Indeed, if you set up another site, say an SSL one on port 443, then it would make sense to put it's NameVirtualHost *:443 in its virtual site config.
 
Sorry for waffling...!
 
Mathew
 
P.S. I missed your initial question - the Include line should go in apache2.conf as this is the 'main' server config file - this line then tells Apache to also include the site-specific config for any enabled sites.

---

### Post by captnops on 2007-10-19
Thanks for all the clarification.

I have setup the system as directed, but the only way I can get the second virtual host site to come up is if I disable the default first site.

Any thoughts on how to remedy this?

Thanks

Todd

---

### Post by MJN on 2007-10-19
If you post the output of **more /etc/apache2/sites-enabled/*** then we can take a look at at what might be wrong.

Mathew

---

### Post by babajc on 2008-05-04
> **captnops said:**
> Can anyone point me to a step by step for creating and hosting virtual name based hosts.

I have STFA and every answer appear to be at odds with every other.

I have apache2.conf not httpd.conf
I have the /etc/apache2/sites-available/default.conf

My understanding of the steps is this:

1.  Add the NameVirtualHost * to the default file in sites-available
2. Add .conf files for each site to host.

I receive the following error when restarting apache:

NameVirtualHost *:0 has no VirtualHosts

Any help is greatly appreciated.  :confused:


See if this post helps:
[http://apachehelp.blogspot.com/2008/05/named-virtual-hosts-in-apache2.html](http://apachehelp.blogspot.com/2008/05/named-virtual-hosts-in-apache2.html)

---

### Post by clw3388 on 2008-07-09
> **captnops said:**
> Thanks for all the clarification.

I have setup the system as directed, but the only way I can get the second virtual host site to come up is if I disable the default first site.

Any thoughts on how to remedy this?

Thanks

Todd

I ran into this same problem.. the catch is on the symlink thing.. i cant explain why but you have to a2dissite the default then a2ensite it ... I never ran into this except on ubuntu ...

---


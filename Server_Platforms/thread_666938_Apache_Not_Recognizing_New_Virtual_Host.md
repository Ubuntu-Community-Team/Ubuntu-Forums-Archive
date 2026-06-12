---
title: "Apache Not Recognizing New Virtual Host"
date: 2008-01-13
forum: Server Platforms
---

### Post by sog on 2008-01-13
Ok, this one is beyond me. Especially since doing the exact same thing not two days ago worked just fine.

Situation is this:

* Dapper LAMP server 
* Running Apache2 
* All five domains point to the machine's IP
* Supporting a primary domain off /var/www 
* Supporting four other domains at various subdirectories via /etc/apache2/sites-enabled
* Files in /etc/apache2/sites-enabled are named 000-default, 001-domain1, etc - where domain1 = the actual domain name

Attempted to add a sixth just by cp'ing and updating one of the previously existing Virtual Hosts template files (sanitized version below), and restarting Apache. This exact process worked as mentioned two days ago for one of the sites in question. 

Unfortunately, the domain still resolves to the primary domain off /var/www, rather than the /var/www/subdirectory it should (there is a working PHP index there). Meaning that the DNS has taken, but the virtual host - for what ever the reason - has not. 

I've been over the virtual host file (006-domain) several times, and recreated it twice, to be sure it's not a simple cut/paste issue. The domain is accurate, but for some reason will not resolve properly, whether one types in domain.com or [www.domain.com](www.domain.com). 

My conclusion is that for some reason the hosts file is not being parsed or digested properly, and therefore a request still resolves to the IP given. What I can't figure out is why, seeing as this domain is no different than any of the other five currently resolving to their proper directories properly. 

Any help, thoughts, insights or solutions appreciated. Anything, as I'm fresh out of ideas.


=====


The text of the Virtual Host file, located in /etc/apache2/sites-enabled and named 006-domain. The "domain" should be read as a string substitute for the actual domain, which has been redacted. 


<VirtualHost *>

        # domain.com
        # Including [www.domain.com](www.domain.com)

        ServerName [www.domain.com](www.domain.com)
        ServerAlias domain.com

        ServerAdmin [email]email@primarydomain.com[/email]

        DocumentRoot /var/www/subdirectory
        <Directory />
                Options FollowSymLinks
                AllowOverride All
        </Directory>

        <Directory /var/www/subdirectory>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

</VirtualHost>

---

### Post by metoor30 on 2008-01-14
Stupid question, but did you clear your browser cache?

---

### Post by Vinno on 2008-01-14
> **sog said:**
> 
<VirtualHost *>

        # domain.com
        # Including [www.domain.com](www.domain.com)

        ServerName [www.domain.com](www.domain.com)
        ServerAlias domain.com

        ServerAdmin [email]email@primarydomain.com[/email]

        **DocumentRoot /var/www/subdirectory**
        <Directory />
                Options FollowSymLinks
                AllowOverride All
        </Directory>

        **<Directory /var/www/subdirectory>**
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

</VirtualHost>

Try it with a **/** e.g /var/www/subdirectory/

---

### Post by sog on 2008-01-15
@metoor30: not a dumb question at all. unfortunately, the answer is yes, i've tried that. also tried different browsers on different machines. same deal. 

@Vinno: great suggestion, but sadly no joy. same deal.

---

### Post by conjur3r on 2008-01-15
On your webserver, what do you get with the domain that's not working:

# host domain.com

---

### Post by sog on 2008-01-15
@conjur3r: on the server, host domain.com returns:

domain.com has address 12.34.567.890

where 12.34.567.890 = the correct IP address, and the same IP that the other domains currently share. a host parentdomain.com, for example, returns the same thing.

---


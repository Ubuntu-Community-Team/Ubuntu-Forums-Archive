---
title: "Virtual hosts go to root www folder"
date: 2007-10-29
forum: Server Platforms
---

### Post by herbie_popnecker on 2007-10-29
I'm not sure what I did, but all of a sudden all requests for virtual hosts go to the root /var/www folder instead of their defined folders. The only clue I get is from an apache restart that gives the warning:

Virtual host overlap on port 80, the first has precedence

Now so I don't get asked the wrong questions:
the conf files are there under /etc/apache2/sites-available
and the links are there under /etc/apache2/sites-enabled

I was in the process of moving sites to a new Ubuntu 6.10 server, and they were working fine, now none are. A main file must have gotten altered, but I have no idea which one.

Any suggestions?

---

### Post by MJN on 2007-10-29
Post the full output of /etc/apache2/sites-enabled/*

As the error states there is a duplicate of eligible virtual host configs and no means to distinguish between them (hence the default fallback of ordered priority),

Mathew

---

### Post by herbie_popnecker on 2007-11-02
000-default                                    
area250.com.conf                            
nakalbun.com.conf                     
[www.fishbc.info.conf](www.fishbc.info.conf)             
[www.propertybc.info.conf](www.propertybc.info.conf)
[www.bcoutdoors.info.conf](www.bcoutdoors.info.conf)                   
[www.rvbc.info.conf](www.rvbc.info.conf)
[www.beetlewood.info.conf](www.beetlewood.info.conf)                      
[www.sleepingdeadgirl.com.conf](www.sleepingdeadgirl.com.conf)
[www.beyondhope.ca.conf](www.beyondhope.ca.conf)                          
[www.softwoodbc.info.conf](www.softwoodbc.info.conf)
[www.beyondhope.info.conf](www.beyondhope.info.conf)               
[www.bluepine.info.conf](www.bluepine.info.conf)                
[www.fortstjames.info.conf](www.fortstjames.info.conf)        
[www.canadarv.info.conf](www.canadarv.info.conf)                             
[www.canoecanada.info.conf](www.canoecanada.info.conf)                          
[www.chilcotin.info.conf](www.chilcotin.info.conf)                     
[www.chundoo.com.conf](www.chundoo.com.conf)                  
[www.nechako.info.conf](www.nechako.info.conf)            
[www.vacationbc.info.conf](www.vacationbc.info.conf)

---

### Post by MJN on 2007-11-02
Sorry, I meant the contents of the files. (Although given the size of the list let's just stick with 000-default and a random one of your choice, assuming they're all configured the same)

Mathew

---

### Post by herbie_popnecker on 2007-11-02
here is sites-enabled/000-default

```

NameVirtualHost *:80
<VirtualHost *:80>
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
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
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
ServerName dax.maxit.net

</VirtualHost>

```
 and one of the virts
```

<VirtualHost *:80>
DocumentRoot "/var/www/web49/web/"
ServerName www.fishbc.info
ServerAlias fishbc.info
<Directory "/var/www/web49/web/">
allow from all
Options +Indexes
</Directory>
</VirtualHost>

```

---

### Post by k_grdn on 2007-11-02
Hi herbie_popnecker,

Try:

Replace: NameVirtualHost *:80 with NameVirtualHost *

Replace all occurences of  <VirtualHost *:80> with <VirtualHost *>

Regards,

k_grdn

---

### Post by herbie_popnecker on 2007-11-02
Arggh Thank you Thank you......

I have no idea why I all of a sudden started setting port 80 entering things thru webmin.

6.10 gets it's listen from /etc/apache2/ports.conf

I am more familiar with RH flavors, and I've been told that under Ubuntu 7.10 things have been changed to a more familiar /etc/httpd.conf but I have the feeling the person who told me that may be thinking of Apache1.3, not Apache2

thx again

---

### Post by MJN on 2007-11-05
I see no problem with using the :80 port suffix - it's not telling Apache what port to listen on (as you say this is defined by the Listen directive) but rather matching a name/IP and port combination.

But, if it's working it's working so I guess that's all that matters!

One thing I did notice is that you didn't have a ServerName in one of your configs - you should include this as it eliminates the ambiguity as to which site to serve. In fact, I would've thought this would cause the symptoms you were seeing because if you had two such configs without Servername directives then Apache wouldn't know how to differentiate between them and hence be forced to treat them in order and assume priority for the first.

Mathew

---

### Post by herbie_popnecker on 2007-11-06
Funny thing is, I am moving two domains to a different server running Fedora. Suddenly, they started doing the same thing!
The only common factor was: it happened entering Virtualhosts thru Webmin.....
I used to just manually add them to httpd.conf on the old server and all my problems started trying to find an easier way!

---


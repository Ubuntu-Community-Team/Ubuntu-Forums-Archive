---
title: "apache internal network"
date: 2008-01-29
forum: Server Platforms
---

### Post by gishaust on 2008-01-29
Hi everyone

I am trying set up a virtual  host that will only work on my  internal network. I can get apache2 to ping through the browser  using an ip address. But is their a way to add a domain name to it. I have tried this with virtual hosts. I am trying to get away from webmin and my learning curve is going up. But i am a little lost! I have the feeling that I will need a domain server for this to work,  is that true.

This is placed at the bottom of my default host file.

<VirtualHost *>
   DocumentRoot /media/data/webpage/pnc
   ServerName  [www.pnc.com](www.pnc.com)
</VirtualHost>

I placed it in the bottom and then restarted apache I got the following error. I don't think the error is coming from what i have setup as it was doing that before. But I have placed it in just in case.

apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (no pid file) not running

Any direction would be greatly received,

gishaust

---

### Post by freebeer on 2008-01-29
Probably the quickest, easiest way (if there's not to many client computers) is to add an entry in their hosts file.

IPaddyofServer  name

is the format.

What this does is that whenever someone types in a URL, the system first looks for the name in the hosts file.  If it finds it, it substitutes the IP address that you've supplied.  If it doesn't find the name, then it looks to a DNS server to get that address.  For a small internal network such as you describe, having a private DNS server is probably overkill.  :)

---

### Post by gishaust on 2008-01-29
thanks for the relpy

there are only two client computers but one is a xp box how do I add that to the hosts in a xp box

---

### Post by tradegame on 2008-01-30
Edit the file at %windir%\system32\drivers\etc\hosts

---

### Post by MJN on 2008-01-30
The ServerName warning suggests your directive is not being picked up - otherwise it would not have to assume what its name is.
 
Post your Apache config as I am curious as to where you've put those directives.
 
Incidentally, is [pnc.com]("http://www.pnc.com") really your domain name? (Not that it really matters - but it's usually a bad idea to use a valid Internet domain on an internal network.... it will turn around and bite you at some stage down the road).
 
Mathew

---

### Post by gishaust on 2008-01-31
Thanks for your replys

I place the information in this file
sudo nano /etc/apache2/sites-available/default

If this is what you mean by the apache config or do you mean you want to see apache2.conf

gishaust

---

### Post by MJN on 2008-01-31
I was wondering where you'd put ServerName - that file is correct. Post the config, and the output when you run **sudo /etc/init.d/apache2 restart**

Mathew

---

### Post by gishaust on 2008-01-31
This is the default file
```
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
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

<VirtualHost *>
DocumentRoot /media/data/webpage/
ServerName www.pnc.com
</VirtualHost>

```

The output is this

```

 * Forcing reload of web server (apache2)...                                                             apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                                                  [ OK ]


```

and I will change the domain name

I hope this is what you are looking for

gishaust

---

### Post by MJN on 2008-02-01
The problem is you've got two sites there - the first (default) living in /var/www/ and the second ([www.pnc.com](www.pnc.com)) living in /media/data/webpage ....

However, only the second has a name - you need to put a ServerName directive in the default config also.

Note however that the 'error' was more of a warning - telling you what assumption it had made in the lack of being provided the info. However, it is important to avoid ambiguities with this particularly for redirects when server names become critical.

If the default site really doesn't have a name then just call it localhost.localdomain. Being the first/default site it will still respond to requests by IP address.

Mathew

---


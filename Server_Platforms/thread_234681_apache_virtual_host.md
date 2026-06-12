---
title: "apache virtual host"
date: 2006-08-11
forum: Server Platforms
---

### Post by davham on 2006-08-11
Hi all
I've been trying to set up apache to host two sites.
I created two folders in /var/www/onesite and /var/www/twosite

In sites-available I have conf files for both sites
#NameVirtualHost *
<VirtualHost *>
        Servername onesite.com
        
        DocumentRoot /var/www/onesite
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/onesite>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
"onesite" 48L, 1192C                                           1,1           Top


 and twosite's is the same

I then made symlinks with a2ensite, did a restart and a reload of apache.

Now when I try them, I get the directory index of /var/www. I know I'm missing something simple, but right now I can't see it.

Any help would be greatly appreciated

ps Ubuntu 6 Dapper Drake

Thanks 
David

---

### Post by chrisfay on 2006-08-11
Put them in /sites-enabled/000-default

And make sure the option is uncommented in apache2.conf:

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/[^.#]*

---

### Post by az on 2006-08-11
RedirectMatch ^/$ /apache2-default/

Do you have the default site enabled as well?  Because its' redirect match is commented out by default and so you get the document root index.

---

### Post by davham on 2006-08-11
I added them to default, which I also had enabled. I had just taken out the index.html page.

Now I get one of the sites but the other shows the apache redirect page. I just did a quick container

<VirtualHost *>
ServerName one
DocumentRoot /var/www/one
</VirtualHost>

for both if them in the default site

---

### Post by davham on 2006-08-11
Well I got it sorted out, not a 100% sure how
I had three sites in sites-available
default 
onesite 
twosite

default had a server name of one site (the simple thing I was overlooking)

onesite had server name of onesite
twosite had server name of twosite
 
I changed the server name in default to localhost, commented out the redirect in all the sites cofigs and did a reload. Now they all go to the sites they're supposed to.

Thanks for your help guys

David

---


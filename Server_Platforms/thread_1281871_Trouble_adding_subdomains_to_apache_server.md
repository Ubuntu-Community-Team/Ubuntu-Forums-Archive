---
title: "Trouble adding subdomains to apache server"
date: 2009-10-03
forum: Server Platforms
---

### Post by crewe on 2009-10-03
Hi this has beeing giving be trouble for a few months now, been trying to find a solution via the "Google" route and now I'm here.

I have a single LAMP server running Ubuntu server.
It currently has two FQDN that work fine via the a2ensite etc. but I I've been wanting to set up a subdomain on one of them but to no avail.

My first major issue is that if I try to navigate to git.site1.com I can't access the page (no ping). If I could just get a connection I might be able to figure it out from there. I know this can all be worked around but just putting a directory within my currently working hosts but a) I don't want that and b) I want to know how to do this for the future.

Any help's appreciated.

here's my http.conf
```

  1 NameVirtualHost *
  2 <VirtualHost *>
  3         ServerName www.site1.com
  4         ServerAlias site1.com *.stie1.com
  5         DocumentRoot /var/www/site1.com
  6 </VirtualHost>
  7 
  8 <VirtualHost *>
  9         ServerName www.site2.com
 10         ServerAlias site2.com *.site2.com
 11         DocumentRoot /var/www/site2.com
 12 </VirtualHost>
 13 
 14 <VirtualHost *>
 15         ServerName git.site1.com
 16 
 17         <Location /repo.git>
 18                 DAV on
 19                 AuthType Basic
 20                 AuthName "git Repository"
 21                 AuthUserFile /etc/apache2/passwd.git
 22                 Require valid-user
 23         </Location>
 24 </VirtualHost>

```

and my apache2 site file from sites-available:
```

  1 <VirtualHost *>
  2         ServerAdmin admin@site1.com
  3         ServerName git.site1.com
  4 
  5         DocumentRoot /var/www/git
  6         <Directory />
  7                 Options FollowSymLinks
  8                 AllowOverride None
  9         </Directory>
 10         <Directory /var/www/git>
 11                 Options Indexes FollowSymLinks MultiViews
 12                 AllowOverride All
 13                 Order allow,deny
 14                 allow from all
 15         </Directory>
 16 
 17         ScriptAlias /cgi-bin/ /var/www/cgi-bin/
 18 
 19         LogLevel warn
 20 
 21         ServerSignature Off
 22 
 23     Alias /doc/ "/usr/share/doc/"
 24     <Directory "/usr/share/doc/">
 25         Options Indexes MultiViews FollowSymLinks
 26         AllowOverride None
 27         Order deny,allow
 28         Deny from all
 29         Allow from 127.0.0.0/255.0.0.0 ::1/128
 30     </Directory>
 31 
 32 </VirtualHost>

```

---

### Post by Vegan on 2009-10-03
I just wrote an article on my site on setting up Apache, go look in my forum, too lazy to get a direct link.

---

### Post by crewe on 2009-10-03
Only difference I saw was that the server's IP and port are added to each vhost, I did that and it still doesn't work.

---

### Post by Vegan on 2009-10-03
I see you are hppt.conf and that is not the place to be putting vhosts. Put them in separate files in /etc/apache2/sites-available

---

### Post by crewe on 2009-10-04
Okay so now I'm not using http.conf except to describe the virtual hosts.
I have three sites in the sites enabled. They all work on the 
the two that always worked still work, but I still have host not found
for git.site1.com.

**http.conf**
```

NameVirtualHost IP.IS.IN.HERE:80

```

**git.site1.com**
```

<VirtualHost IP.IS.IN.HERE:80>
        ServerAdmin admin@site1.com
        ServerName git.site1.com

        DocumentRoot /var/www/git
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/git>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /var/www/cgi-bin/
        LogLevel warn
        ServerSignature Off

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
</VirtualHost>

```

---

### Post by volkswagner on 2009-10-04
How are you handling DNS?  Did you add the subdomains to your DNS provider?

---

### Post by crewe on 2009-10-04
easydns is my DSN provider, however, this may sound ignorant, but nowhere did I ever find in tuts that I had to make mods to my DNS config on my provider = [. I guess this was implied, but even so I don't know how to do it. The ANAME, CNAME stuff throws me and last time I modified it, it took my sites down. I'd email them but I won't get a reply until Monday, and I won't be able to do anything with it until late Monday or Tuesday... 
Any general pointers?

---

### Post by exww on 2009-10-04
add a cname record for sub.site.com pointing to @ (your server ip)

---

### Post by crewe on 2009-10-04
Okay I got it, did some tweaking on the back end of the DNS provider page and all is well, thanks for the help.

---


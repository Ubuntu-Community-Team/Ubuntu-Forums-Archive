---
title: "multiple Virtual Hosts with Apache 2"
date: 2005-11-10
forum: Server Platforms
---

### Post by OneSeventeen on 2005-11-10
I have Apache 2 installed on my ubuntu server, and it works great for my webserver as of now, but I'd also like to add a few more domain names to it.

According to the manual Virtual Hosts are set up like this:
```

 NameVirtualHost *:80

<VirtualHost *:80>
ServerName www.domain.com
DocumentRoot /www/domain
</VirtualHost>

<VirtualHost *:80>
ServerName www.otherdomain.com
DocumentRoot /www/otherdomain
</VirtualHost>

```

But the default Ubuntu installation doesn't even have my ServerName listed, I'm assuming because it doesn't know it during the time of installation, and that's up to me.

Should I
[LIST=a]
[*]Copy and paste the VirtualHost data that exists, and add the ServerName to each one, or
[*]Create a new file in the sites-available folder, and add ServerName to it, and the default, then symlink it to the sites-enabled folder?
[/LIST]

I'm still not used to how the configs are set up, but they are supposedly designed for ease of use, so I'd hate to throw that ease of use out the window just because I did "what works" and didn't ask for a proper way of doing it :)

---

### Post by LordHunter317 on 2005-11-10
You create a file per-virtual host in sites-available, then symlink into sites-enbaled (or use a2ensite), perhaps changing the order if needed.

You can use the existing virtual host as a template, or provided your own.  

Note that whatever virtualhost is processed first will be the site peopel are directed to when Apache can't figure out where to go.

---

### Post by OneSeventeen on 2005-11-10
cool!  That works great!
I just did:
cp /etc/apache2/sites-available/default /etc/apache2/sites-available/new
then changed the new file by removing the first line:
```
#NameVirtualHost *
```
And inside the <virtualhost=*> tags I added:
```

<VirtualHost *>
        ServerAdmin webmaster@newsite.com
        ServerName newsite.com
        DocumentRoot /path/to/site
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /path/to/site>
                Options Indexes FollowSymLinks MultiViews
.....................snip....................

```

I restarted apache and it didn't work :(  then I changed the ServerName to the proper domain and restarted apache again and it worked great!

I left the other file alone so any request to that IP goes to the default site, and I'll just keep copying this new config file for each new site to add to it.  Very easy, thanks again.

---


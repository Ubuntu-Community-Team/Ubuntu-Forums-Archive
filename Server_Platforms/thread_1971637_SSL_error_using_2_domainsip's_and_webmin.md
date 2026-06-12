---
title: "SSL error using 2 domains/ip's and webmin"
date: 2012-05-02
forum: Server Platforms
---

### Post by tangerine0469 on 2012-05-02
ok, so I have my Virtual private server set up for my two domains. i have 2 ip addresses for this and 2 ssl certificate, key files, etc. I use webmin to set it all up and had the two domain names on their own respective ip's and they resolved perfectly. once i turn on the ssl it works like a charm through ssl only...When i take the magical s out of https:// i get the following error:

Bad Request

Your browser sent a request that this server could not understand.
Reason: You're speaking plain HTTP to an SSL-enabled server port.
Instead use the HTTPS scheme to access this URL, please.
Hint: [https://www.john-stapleton.com/](https://www.john-stapleton.com/)
Apache/2.2.17 (Ubuntu) Server at [www.john-stapleton.com](www.john-stapleton.com) Port 443

my webmin config files are as follows:
(domain hidden on the second one as i am not ready to launch the site or name)

Site 1:


> <VirtualHost 173.212.223.96:443>
ServerName [www.john-stapleton.com](www.john-stapleton.com)
<Directory "/var/www/">
allow from all
Options +Indexes
</Directory>
SSLEngine on
SSLCertificateFile /etc/ssl/certs/www_john-stapleton_com.crt
SSLCertificateKeyFile /etc/ssl/private/www.john-stapleton.com.key
SSLCACertificateFile /etc/ssl/certs/www_john-stapleton_com.ca-bundle
DocumentRoot /var/www/john-stapleton_com/www
</VirtualHost>

site 2:



> <VirtualHost 173.212.223.95:443>
DocumentRoot /var/www/newsite_com/www/
ServerName [www.newsite.com](www.newsite.com)
<Directory "/var/www/">
allow from all
Options +Indexes
</Directory>
SSLEngine on
SSLCertificateFile /etc/ssl/certs/newsite.crt
SSLCertificateKeyFile /etc/ssl/private/newsite.key
SSLCACertificateFile /etc/ssl/certs/newsite.ca-bundle
</VirtualHost>


I have tried almost everything from a 301 redirect to mod_rewrite to strict require and most of them give me a 500 internal server error. i have also tried to set these up from the traditional command line only and get the same errors. does anyone know what i am doing wrong here?

---

### Post by SeijiSensei on 2012-05-03
Webmin usually runs its own SSL server on port 10000.  Is that not true for you?  I've never configured Apache to serve Webmin.

---

### Post by tangerine0469 on 2012-05-03
> **SeijiSensei said:**
> Webmin usually runs its own SSL server on port 10000.  Is that not true for you?  I've never configured Apache to serve Webmin.

Webmin does but that does not seem to conflict with my CA ssl files for the virtual host. My problem is when someone accesses the site via http connection the standard methods of redirect do  not work. Try it out, the URL is [www.john-stapleton.com](www.john-stapleton.com). Try it both in http and https.

---

### Post by SeijiSensei on 2012-05-03
I just use a Redirect in those cases:

```

<VirtualHost *:80>
ServerName    www.example.com
Redirect      / https://www.example.com/
</VirtualHost>

```

---

### Post by tangerine0469 on 2012-05-03
i am still getting the same error no matter where i put the redirect, with or without permanent. i tried in the same virtualhost file and in a separate one, then i tried on port 80 and * in both files, i am just not getting this and i know it is dreadfully simple.

---

### Post by SeijiSensei on 2012-05-04
You need four virtual host definitions, two for the sites on port 80 with a ServerName, optional ServerAlias, and a Redirect and nothing else, and two for the sites on port 443 as you have now.

---

### Post by tangerine0469 on 2012-05-04
> **SeijiSensei said:**
> You need four virtual host definitions, two for the sites on port 80 with a ServerName, optional ServerAlias, and a Redirect and nothing else, and two for the sites on port 443 as you have now.

I ended up trying that first as that was part of the walk through i used to do it (ssl is not my strong point). It turns out in the base setup it had NamedVirtualHost directive enabled in the ports.conf file and by commenting out that directive i fixed the issue. Very small bug that stopped my server i its tracks. 

and just to make sure though, from this point on if i were to add a new domain/sub-domain i would need a new ip and essentially just copy the exact setup save the file/domain names?

---

### Post by SeijiSensei on 2012-05-04
If you want SSL on every site, then yes.  In general you need a separate IP for each SSL site.  For ordinary HTTP sites, you can use a single IP and name-based virtual hosting.

---

### Post by tangerine0469 on 2012-05-04
ok, thanks again. i figured as much but i just wanted to make sure. the whole ssl issue has thrown doubts in to my head.

---


---
title: "1 domaine name and 3 servers"
date: 2013-08-07
forum: Server Platforms
---

### Post by alfirdaous on 2013-08-07
Hello everybody,

I've got 3 servers, I would like to attache them to 1 domain name, 1 main domain and 2 subdomains:

I am looking for something like this:

```

www.domaine.com
server2.domaine.com
server3.domaine.com

```

What I did in server1:

I created a file /etc/bind/db.domaine.com

```

; domaine.com
$TTL    3600
@   IN  SOA hostName.kimsufi.com. root.domaine.com. (
            2011020907 ; SERIAL
            3600; REFRESH
            15M; RETRY
            1W; EXPIRE
            600 ) ; Negative Cache TTL
;
; NAMESERVERS
;
domaine.com. IN       NS       hostName.kimsufi.com.
domaine.com. IN       NS       ns.kimsufi.com.
;
; Nodes in domain
;
www       IN A         IP_SERVER1
mail      IN A         IP_SERVER1
ns1       IN A         IP_SERVER1
smtp      IN A         IP_SERVER1
pop       IN A         IP_SERVER1
ftp       IN A         IP_SERVER1
imap      IN A         IP_SERVER1
domaine.com.   IN  A   IP_SERVER1
server2.domaine.com. IN A IP_SERVER2
server3.domaine.com. IN A IP_SERVER3
domaine.com.   IN  MX  10 mail.domaine.com.
;
; subdomains
;
*.domaine.com. IN A IP_SERVER1

```

bind9: /etc/bind/named.conf.local

```

zone "domaine.com" {
    type master;
    file "/etc/bind/db.domaine.com";
    allow-transfer {IP;};
    allow-query{any;};
    notify yes;
};

```

virtual host: /etc/apache2/sites-available/domainecom

```

<VirtualHost *:80>
        ServerAdmin account@gmail.com
        ServerName www.domaine.com
        ServerAlias domaine.com
        DocumentRoot /home/server1/www
        DirectoryIndex index.php index.html
        <Directory />
                Options FollowSymLinks
                AllowOverride All
        </Directory>
        <Directory /home/server1/www/>
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

</VirtualHost>

```

And then I restarted apache2 with bind9, 
Enable the site
Disable the default site

The same configuration goes for server2 and server3, once I joined to: server2.domaine.com and server3.domaine.com, It displays the index of [www.domaine.com](www.domaine.com), basicaly I should have the index of server2 and server3

Thx for your help

---

### Post by SeijiSensei on 2013-08-07
When you say you have "three servers" are these three separate machines?  The configuration you're trying to set up uses only one machine.

---

### Post by alfirdaous on 2013-08-12
they are 3 seperated machines with 3 IP addresses, I am setting up the configuration for three of them

---

### Post by SeijiSensei on 2013-08-12
Name each machine to match the fully-qualified domain name of each site.  So one machine might be "www.example.com," the next "secure.example.com," and the last "webmail.example.com".  Make sure there are corresponding DNS entries for each hostname/IP pair.  Then just configure each machine to serve the site it represents.

---

### Post by alfirdaous on 2013-08-12
are there some mods to be enabled so that will work fine?

---

### Post by SeijiSensei on 2013-08-13
No.  Why don't you give it a try?  Experimentation is often the fastest way to learning.

---

### Post by alfirdaous on 2013-08-13
I enabled rewrite mod and now it works great

Thx for your help

---


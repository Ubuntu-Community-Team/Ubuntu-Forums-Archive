---
title: "dig resolves my ipv6 domain, nslookup fails"
date: 2010-03-20
forum: Server Platforms
---

### Post by rukiaEnix on 2010-03-20
hello I don't understand why this is happening:
my ipv6 is: 2002:a09:807::204:acff:fe66:7d47    and everything works fine with it, but:
```

dig ipv6.domain.com  //works
nslookup ipv6.domain.com //fails
nslookup 2002:a09:807::204:acff:fe66:7d47  //works

```here is my domain zone configuration:
```

;
; BIND data file for local loopback interface
;
$TTL    604800
@    IN    SOA    ipv6.domain.com. root.ipv6.domain.com. (
                  2        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;

            NS    debian.ipv6.domain.com.
IN         AAAA    2002:0a09:0807:0000:0204:acff:fe66:7d47

```inverse zone:
```

;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@    IN    SOA    ipv6.domain.com. root.ipv6.domain.com. (
                  1        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
@                                IN  NS    ipv6.domain.com.
7.4.d.7.6.6.e.f.f.f.c.a.4.0.2.0    IN  PTR    ipv6.domain.com.

```what I don't understand is why dig works and nslookup doesn't?
and configuring apache2 with this domain doesn't work either

---

### Post by HermanAB on 2010-03-20
Howdy,

Nslookup is deprecated.  It is buggy and should not be used.

---

### Post by rukiaEnix on 2010-03-20
yes I've already read that dig is replacing nslookup but still my problem is this:
dig resolves my ipv6 domain but:
apache can't resolve it 

here is my apache2 configuration:
```

NameVirtualHost ipv6.domain.com
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

```

my ports.conf file:
```

Listen [::]:80

```

---


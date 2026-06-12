---
title: "Apache Virtual hosts"
date: 2005-08-23
forum: Server Platforms
---

### Post by nocturn on 2005-08-23
I'm trying to get my (internal) Apache server to serve a couple of virtual hosts.
I created some files in .../sites-available and enabled them, but something is going wrong.

Some hosts have SSL protection on, but for some strange reason all hosts use the same certificate, although the certificates are specified per virtual host.  If I disable one host, the certificates of the next are used...

What is the correct way to do this?

---

### Post by LordHunter317 on 2005-08-23
You do have them using a different IP for each host, right?  And a different DNS name, right?

And you setup the SSL configuration per each <VirtualHost> directive right, and didn't like set it globally?

Posting your configurations would be the eaisest way.

---

### Post by nocturn on 2005-08-23
[QUOTE=LordHunter317]You do have them using a different IP for each host, right?  And a different DNS name, right?
[/quote]

No, they are on a single machine with one IP address.  They do have different DNS names (but recursive queries map to the real hostname).


> 
And you setup the SSL configuration per each <VirtualHost> directive right, and didn't like set it globally?

Posting your configurations would be the eaisest way.

```

NameVirtualHost subversion.home.vsb:443
<VirtualHost subversion.home.vsb:443>
        ServerAdmin root@home.vsb
        ServerName subversion.home.vsb

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

        SSLEngine on
        SSLCertificateFile /etc/apache2/ssl/subversion.pem
        SSLCertificateKeyFile /etc/apache2/ssl/subversion.key
</VirtualHost>

```

```

NameVirtualHost intranet.home.vsb:443
<VirtualHost intranet.home.vsb:443>
        ServerAdmin root@home.vsb
        ServerName intranet.home.vsb

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
                # Commented out for Ubuntu
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        SSLEngine on
        SSLCertificateFile /etc/apache2/ssl/intranet.pem
        SSLCertificateKeyFile /etc/apache2/ssl/intranet.key
</VirtualHost>

```

---

### Post by LordHunter317 on 2005-08-23
[QUOTE=nocturn]No, they are on a single machine with one IP address.[/quote]Can't do this.  SSL requires different IP addreses per site, as the certificate can be tied only to one domain name.

When you do Name-Based virtual hosting, the DNS name of the host taht's really wanted at that IP address is included in the HTTP request.  This is what allows multiple sites with different names at the same IP.

However with SSL, the encryption begins before the HTTP request is even sent.  The authenticity of SSL prevents name-based virtual hosting from functioning.

> They do have different DNS names (but recursive queries map to the real hostname).What, are you saying they're all CNAMES?

You're going to have to use different IP addresses.  Then it will work.  What apache is doing now is exactly what it should do: using the first virtual host on an address as the default.

---

### Post by nocturn on 2005-08-24
[QUOTE=LordHunter317]Can't do this.  SSL requires different IP addreses per site, as the certificate can be tied only to one domain name.

When you do Name-Based virtual hosting, the DNS name of the host taht's really wanted at that IP address is included in the HTTP request.  This is what allows multiple sites with different names at the same IP.

However with SSL, the encryption begins before the HTTP request is even sent.  The authenticity of SSL prevents name-based virtual hosting from functioning.
[/quote]

Thanks for this, that'll be the cause of my problems.

> 
What, are you saying they're all CNAMES?


I always set up my server with a hostname (like cronos) and then create DNS aliases for most functions (cups, subversion, mail, ...).

---

### Post by LordHunter317 on 2005-08-24
For SSL, ideally you'll need to convere those CNAME records to A records, and use the A record on the SSL certificate and to access the site.  Also, make sure your RDNS records point to the proper A records as well.

---

### Post by nocturn on 2005-08-25
Thanks for the help.

---


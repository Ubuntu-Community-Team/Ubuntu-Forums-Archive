---
title: "[SOLVED] VirtualHosts with XAMPP"
date: 2008-03-11
forum: Server Platforms
---

### Post by Dr Small on 2008-03-11
XAMPP runs Apache, so don't let that throw you off. I am determined to get this figured out, and I really need somebody's help who knows what they are doing.

I have 2 subdomains hosted at DynDNS.org pointing to my IP Address. I really don't want anyone going to the right yet, so we'll use fake names.

Subdomain 1: site1.homelinux.org
Subdomain 2: site2.homelinux.org

Ok, so now that they both point to my IP address of (123.456.789... for example) and I want site1.homelinux.org to point to /opt/lampp/htdocs (the default www directory) and site2.homelinux.org to point to /var/ftp.

Ok. That's simple enough, right?
Well, I have yet to figure it out.

Here is what I have in my /opt/lampp/etc/extra/httpd-vhosts.conf file:
```
<VirtualHost *:80>
        ServerAdmin drsmall@mycroft
        DocumentRoot /var/ftp/
        ServerName site2.homelinux.org
        ServerAlias www.site2.homelinux.org
</VirtualHost>

<VirtualHost *:80>
        ServerAdmin drsmall@mycroft
        DocumentRoot /opt/lampp/htdocs/
        ServerName site1.homelinux.org
        ServerAlias www.site1.homelinux.org
</VirtualHost>

```

Then I restarted apache:
```
sudo /opt/lampp/lampp reloadapache
```

And I went to both site1.homelinux.org and site2.homelinux.org and they are both taking me to /opt/lampp/htdocs/.

What am I doing wrong?

Dr Small

---

### Post by Dr Small on 2008-03-11
I edited /opt/lampp/etc/httpd.conf, uncommented:
```
# Virtual hosts
#Include etc/extra/httpd-vhosts.conf

```

Restarted Apache, and now I can access the differenet diretories with the subdomains :D

Dr Small

---


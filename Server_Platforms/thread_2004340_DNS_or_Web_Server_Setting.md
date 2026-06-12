---
title: "DNS or Web Server Setting?"
date: 2012-06-15
forum: Server Platforms
---

### Post by pgp_protector on 2012-06-15
I'm running Ubuntu server on a network and I'm setting that up to handle the incoming web request on port 80 from our DSL Line.  So the router sends all port 80 request to our Ubuntu server.  

This part is working so far, so good.

Now the problem.
We also have a Windows Home Server (Backup storage & system backups), this works internally.
So if I try to go to mywindowsserver.homeserver.com  the Ubuntu DNS Server points me to my homeserver (192.168.1.78) without issue.

But, if I try to access it from outside our network, I get my Ubuntu Default page, and it's not directed to 192.168.1.78 

So is this a DNS Issue or do I also have to change / add a setting in Apache?

---

### Post by SeijiSensei on 2012-06-15
Set up a virtual host in Apache that passes requests to the other server using [mod_proxy](http://httpd.apache.org/docs/2.2/mod/mod_proxy.html).

---

### Post by pgp_protector on 2012-06-15
So Something like this ? on my Ubunu Apache Server should work ?

<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName mywindowsserver.homeserver.com

    ProxyRequests Off
    <Proxy *>
            Options Indexes FollowSymLinks MultiViews
            AllowOverride all
            Order allow,deny
            allow from all
    </Proxy>

    ProxyPass / [http://192.168.1.79](http://192.168.1.79)
    ProxyPassReverse /  [http://192.168.1.79](http://192.168.1.79)
    LogLevel debug

    CustomLog ${APACHE_LOG_DIR}/api_access.log combined
    ErrorLog ${APACHE_LOG_DIR}/api_error.log
</VirtualHost>

---

### Post by cartaysm on 2012-06-15
Dont know if this will help in your situation, but this is what I use;

[PHP]
<VirtualHost *:80>
DocumentRoot root/mysite
ServerName mysite
ServerAlias www.mysite
<Directory "root/mysite">
Options Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
allow from all
DirectoryIndex Home.php
</Directory>
</VirtualHost>

<VirtualHost *:80>
DocumentRoot root/mysite2
ServerName mysite2
ServerAlias www.mysite2
<Directory "root/mysite2">
Options Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
allow from all
DirectoryIndex Login.php
</Directory>
</VirtualHost>
[/PHP]

---

### Post by pgp_protector on 2012-06-18
Ok if I'm using the Mod_Proxy, do I use / keep any settings in the DNS Zones for the site ?

---

### Post by SeijiSensei on 2012-06-18
As long as there is a unique public DNS entry for the virtual server that you're routing to Windows, no.  You need a separate entry for each virtual server name even though they both point to the same address.  With "name-based" virtual hosts, Apache determines which <VirtualHost> definition to use based on the server name given in the URL.  See [http://httpd.apache.org/docs/2.2/vhosts/name-based.html](http://httpd.apache.org/docs/2.2/vhosts/name-based.html) for details.

So in the DNS you might have records in the zone file for example.com like:

```

www               IN  A     10.10.10.10
anotherserver     IN  CNAME www

```

The CNAME is an alias definition.  You could alternatively have an A record for "anotherserver" with the identical IP address.  CNAME aliases make it easier to handle changes in IP addresses since you only need to change one record.

---

### Post by pgp_protector on 2012-06-19
almost had it :mad:
```

<VirtualHost *:80>
ProxyPreserveHost on
ProxyRemote / http://192.168.1.78
ProxyPassReverse / http://192.168.1.78
ServerName windowsserver.homeserver.com
</VirtualHost>

```

From my reading should of worked, but I'm getting a 403 error when I try to get their now (Both on site & off site)

And log is showing this error ? :confused:
[Tue Jun 19 2012] [error] [client xxx.xxx.xxx.xxx] client denied by server configuration: /etc/apache2/htdocs

---

### Post by SeijiSensei on 2012-06-20
Check your virtual hosts.  Something must be referencing /etc/apache2/htdocs, a folder that doesn't exist in a stock Ubuntu build.

One quick test is to grep for htdocs like this:

```

cd /etc/apache2
sudo grep 'htdocs' *
sudo grep 'htdocs' */*

```

You should see any files and matching lines where it is referenced.

Is this a vanilla installation of Ubuntu or Ubuntu Server and a vanilla apache2?  Did you try following some online tutorial that might have had you configure something to use /etc/apache2/htdocs?  As I say, it's not a directory that's part of a standard Ubuntu installation of apache2.

---

### Post by pgp_protector on 2012-06-21
> **SeijiSensei said:**
> Check your virtual hosts.  Something must be referencing /etc/apache2/htdocs, a folder that doesn't exist in a stock Ubuntu build.

One quick test is to grep for htdocs like this:

```

cd /etc/apache2
sudo grep 'htdocs' *
sudo grep 'htdocs' */*

```

You should see any files and matching lines where it is referenced.

Is this a vanilla installation of Ubuntu or Ubuntu Server and a vanilla apache2?  Did you try following some online tutorial that might have had you configure something to use /etc/apache2/htdocs?  As I say, it's not a directory that's part of a standard Ubuntu installation of apache2.

Both commands come up blank.

I had followed the tutorial -> [http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3-p2](http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3-p2)
but for the version 11 of ubuntu (What was available when I build the server)

---

### Post by SeijiSensei on 2012-06-23
> **pgp_protector said:**
> I had followed the tutorial -> [http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3-p2](http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3-p2)

I don't see anything there about configuring apache, just how to install Ubuntu.  Is there another page that you followed for apache?

The directory /etc/httpd/htdocs appears in other distributions like RedHat and its clones (CentOS, etc.).  If you build Apache from source it will be installed in /usr/local/etc/httpd with corresponding directory /usr/local/etc/httpd/htdocs.  As I said, none of this applies to Ubuntu, where configurations are stored in /etc/apache2 and the default DocumentRoot is /var/www.

---


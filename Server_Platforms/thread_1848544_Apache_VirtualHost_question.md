---
title: "Apache VirtualHost question"
date: 2011-09-22
forum: Server Platforms
---

### Post by beernutz on 2011-09-22
I have a problem getting two virtualhosts in Apache 2.2.16 under Ubuntu 10.04 to work as I'd like them to work.  If I use the symbolic link naming below, requests to either my IP address or to the ServerName of my virtualhost defined in the bs file will be directed to the DocumentRoot defined in the default virtualhost configuration file.

If I rename the symbolic link 001-bs to 000-bs so that it is processed first, then the exact opposite happens in that requests to either my IP address or to the ServerName of my virtualhost  defined in the bs file will be directed to the DocumentRoot defined in  the bs virtualhost configuration file.

What I can't figure out is how to have the requests directed to my IP address directed to the document root defined in my default configuration file, while at the same time I want the requests which are directed to my servername, bobsmith.info, show be directed to the document root defined in my bs virtualhost configuration file.

It seems that whichever of the two virtualhost configuration files is processed first, as determined by the names of their symbolic links, will be used to handle all requests and the other virtualhost configuration file appears to be ignored.
 
Any constructive help or advice is much appreciated.

ls -l output of /etc/apache2/sites-enabled:
```
total 0
lrwxrwxrwx 1 root root 26 2011-09-21 16:10 000-default -> ../sites-available/default
lrwxrwxrwx 1 root root 30 2011-03-25 17:20 000-default-ssl -> ../sites-available/default-ssl
lrwxrwxrwx 1 root root 21 2011-09-21 16:49 001-bs -> ../sites-available/bs

```apachectl -S output (actual IP address obscured with XXX.XXX):
```

VirtualHost configuration:
192.245.XXX.XXX:80      is a NameVirtualHost
         default server localhost (/etc/apache2/sites-enabled/000-default:1)
         port 80 namevhost localhost (/etc/apache2/sites-enabled/000-default:1)
         port 80 namevhost bobsmith.info (/etc/apache2/sites-enabled/001-bs:1)
192.245.XXX.XXX:443     is a NameVirtualHost
         default server localhost (/etc/apache2/sites-enabled/000-default-ssl:3)
         port 443 namevhost localhost (/etc/apache2/sites-enabled/000-default-ssl:3)
```bs virtualhost configuation file in /sites-available:
```
<VirtualHost 192.245.XXX.XXX:80>
       ServerAdmin webmaster@bobsmith.info
       ServerName bobsmith.info
       ServerAlias www.bobsmith.info

       DocumentRoot /usr/local/htdocs

</VirtualHost>
```default virtualhost configuation file in /sites-available:
```
<VirtualHost 192.245.XXX.XXX:80>
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
    </Directory>
</VirtualHost>

```ports.conf file contents:
```
NameVirtualHost 192.245.XXX.XXX:80
Listen 80

<IfModule mod_ssl.c>
    NameVirtualHost 192.245.XXX.XXX:443
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>
```/etc/hosts contents:
```
127.0.0.1    localhost.localdomain localhost
127.0.1.1       ite453isc553-59
127.0.1.2       bobsmith.info 

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

---

### Post by volkswagner on 2011-09-22
The behavior you mention indicates NameVirtualHosts is not properly working/setup.

You have no ServerName setup in your default.  The way apache works if all vhosts are equal ie: contain the same directive "<VirtualHost 192.245.XXX.XXX:80>", then Apache sorts based in which vhost FileName is alfa/numerically first.

If you add a server name to you default and restart apache you may get it working.  Perhaps use your host name.

```
hostname
```

User the output from the above command and add it to your default vhost file ServerName directive.

This is of course assuming you have a working DNS for the hostnames.

---

### Post by beernutz on 2011-09-27
> **volkswagner said:**
> The behavior you mention indicates NameVirtualHosts is not properly working/setup.

You have no ServerName setup in your default.  The way apache works if all vhosts are equal ie: contain the same directive "<VirtualHost 192.245.XXX.XXX:80>", then Apache sorts based in which vhost FileName is alfa/numerically first.

If you add a server name to you default and restart apache you may get it working.  Perhaps use your host name.

```
hostname
```User the output from the above command and add it to your default vhost file ServerName directive.

This is of course assuming you have a working DNS for the hostnames.
I tried adding a ServerName value to the default virtualhost configuration but that doesn't change Apache's behavior.  I do appreciate the suggestion though.

I think I understand the way Apache is supposed to work, in that it will read the first virtualhost file, as determined by the symlink name in /sites-enabled, but it should also read through the other virtualhost config files looking to match ServerName or ServerAlias values which it doesn't appear to be doing.  It appears from the output of apachectl -S that Apache is reading both configuration files but it is only acting on the settings in the first one it reads.

---

### Post by volkswagner on 2011-09-28
Nothing else really stands out.

The ip address you're using in host and ports.conf files, is that what shows up in

```
ifconfig
```

If you don't need to be listening on multiple interfaces or ip's you can change the vhost and conf files to look like this and restart apache2

For each vhost file
```
<VirtualHost *:80>
```


In ports.conf
```
NameVirtualHost *:80
```

One other thing is you /etc/hosts file.

Does 127.0.1.2 show up in the above call to ifconfig?

If not you should move the entry to look more like this:

```
127.0.0.1    localhost.localdomain localhost
127.0.1.1       ite453isc553-59 bobsmith.info  
```

Is "ite453isc553-59 " your actual hostname ie: output from

```
hostname
```

If not what is it and you should have the output of hostname also listed on the loopback line 127.0.1.1.

---

### Post by Ryan Dwyer on 2011-09-28
Changing all instances of 192.245.XXX.XXX:80 to *:80 should fix it.

In this case bobsmith.info is resolving to a 127.x.x.x address which doesn't match your vhost block. *:80 allows it to listen on everything.

---


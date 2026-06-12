---
title: "Apache does not respond to external requests"
date: 2007-02-05
forum: Server Platforms
---

### Post by pqueiro on 2007-02-05
Hi

I installed Apache 2 on my Xubuntu box and it apparently works as long as I access it from the server itself; if I try to access it from another machine - be it other computers in my network or an external client - it won't answer the HTTP request (and I'm pretty sure I'm forwarding the 80 port like I should :-P).

Any idea what's up?

Thanks :)

---

### Post by jtc on 2007-02-05
Well, one thing we can do is to check whatever apache2 listens to all connections or simply from localhost, or something else. What is the output of the following command

```
sudo netstat -tlp |grep "apache2"
```

Then it might be intressting to see what your /etc/apache2/sites-available/default looks like. Keywords in this case are Allow from and Deny from.

---

### Post by jpeddicord on 2007-02-05
iptables might be blocking port 80. Try installing the firestarter package (assuming this is a GUI desktop you just installed Apache on) to open up port 80, and then try.

---

### Post by pqueiro on 2007-02-05
netstat outputs

```
tcp6       0      0 *:www                   *:*                     LISTEN     5100/apache2
```

whereas sites-available/default contains

```
NameVirtualHost *
<VirtualHost *>
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
                **allow from all**
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
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

```

(bold is mine, of course ;) )

As for the firewall, I installed Firestarter and added a rule that allows everyone to access port 80, but nothing's changed :(

---

### Post by TDave on 2007-02-05
I'm suffering a similar problem, albeit it with a slight twist.

My apache server, with PHP and Mysql has worked solidly for well over a year until yesterday I tried to install and setup a wildfire server as per this guide:
[http://www.subvs.co.uk/installing_wildfire_jabber_server](http://www.subvs.co.uk/installing_wildfire_jabber_server)

Pre-wildfire installation apache was serving publicly, but since the installation (even after I stopped the wildfire daemon again) the server isn't accessible externally for HTTP. SSH and FTP both work fine, as does reaching the admin port for Wildfire.
Using links2 on when SSH-ing into the box shows that localhost works.
Firewall and port forwarding settings on the gateway have stayed the same and are unchanged.

Apache2 ports.conf still listens on 80 (as the links2 localhost test shows) and the outcome of the previously reccomended command is as follows:

```
tcp6       0      0 *:www                   *:*                     LISTEN     4637/apache2  
```

My biggest problem now is that, looking at that, and not having a nice GUI to work with, I'm struggling to see and work out how to work with iptables (which I presume I need to do, although it is a presumption) and, more seriously, I can't work out what part of the installation process of wildfire could have caused this.

Any help anyone can provide whilst I try to translate the iptables docs to something I understand would be appreciated. :-)

TD

---


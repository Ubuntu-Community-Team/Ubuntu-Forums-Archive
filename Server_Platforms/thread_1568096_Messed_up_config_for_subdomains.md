---
title: "Messed up config for subdomains"
date: 2010-09-04
forum: Server Platforms
---

### Post by pino262 on 2010-09-04
[I][U]Hi there, 
This week i switched from wind$ws (wamp)to ubuntu server(lamp) for home development cause wind$ws totally sack cack
Everything is working fine but now i want to add some subdomains.
Im now messing with it for 4 days without any luck and i know i totally messed up the files so its time to ask for some help.
I dunno what to do and want to give up cause i tried everything, and just cant get it working SO PLEASE HELP
Yes vhost_alias is enabled.
Server ip is 192.168.1.33

What i want:[/U][U]
localhost
ftp.localhost
foto.localhost
So here are some configs

I ''a2dissite'' default[/U][U]
ftp enabled
foto enabled
-----------------------------------------------------------
/etc/apache2/sites-available/ftp
```

<VirtualHost *>
        DocumentRoot /var/www/ftp/
        ServerName ftp.localhost

[/U][U]         <Directory /var/www/ftp/>
                Options Indexes FollowSymLinks MultiViews +Includes
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>


```-----------------------------------------------------------[/U][U]
/etc/apache2/sites-available/foto
```

#NameVirtualHost 127.0.0.1
#<VirtualHost 127.0.0.1>
<VirtualHost *>
        DocumentRoot /var/www/foto/
        ServerName foto.localhost

[/U][U]         <Directory /var/www/foto/>
                Options Indexes FollowSymLinks MultiViews +Includes
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>


```-----------------------------------------------------------[/U][U]
My ubuntu SERVER hosts file  /etc/hosts
```

192.168.1.33    ubuntu111.lokaal        ubuntu111
127.0.0.1       localhost
#127.0.0.1       foto.localhost
127.0.0.1       192.168.1.33/foto/
127.0.0.1       ftp.localhost
# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters


```-----------------------------------------------------------[/U][U]

-----------------------------------------------------------[/U][U]
My windows CLIENT hosts file
```

# localhost name resolution is handled within DNS itself.
#    127.0.0.1       localhost
#    ::1             localhost
192.168.1.33        localhost
192.168.1.33        foto.localhost
192.168.1.33        ftp.localhost

```-----------------------------------------------------------[/U][/I]

---

### Post by pino262 on 2010-09-04
While reading my own thread i remembered something else  that i saved on my notepad and i fixed my problem :D

```
**Name-Based Virtual Hosts**
 With name-based virtual hosts, one instance of Apache hosts several  domains. You do not need to set up multiple IPs for a machine. This is  the easiest, preferred alternative. Reasons against the use of  name-based virtual hosts are covered in the Apache documentation.
 Configure it directly by way of the configuration file /etc/apache2/  sites-available/filename(by default we have default name file take this  as reference and create new file). To activate name-based virtual hosts,  specify a suitable directive. NameVirtualHost *. * is sufficient to  prompt Apache to accept all incoming requests. Subsequently, configure  the individual hosts:

 NameVirtualHost *
ServerName www.example.com
DocumentRoot /home/www/htdocs/example.com
ServerAdmin webmaster@example.com
ErrorLog /var/log/apache2/www.example.com-error_log
CustomLog /var/log/apache2/www.example.com-access_log common



 ServerName www.myothercompany.com
DocumentRoot /home/www/htdocs/myothercompany.com
ServerAdmin webmaster@myothercompany.com
ErrorLog /var/log/apache2/www.myothercompany.com-error_log
CustomLog /var/log/apache2/www.myothercompany.com-access_log common

 A VirtualHost entry must also be configured for the domain originally  hosted on the server (www.example.com). In this example, the original  domain and one additional domain (www.myothercompany.com) are hosted on  the same server.
 Just as in NameVirtualHost, a * is used in the VirtualHost  directives. Apache uses the host field in the HTTP header to connect the  request to the virtual host. The request is forwarded to the virtual  host whose ServerName matches the host name specified in this field.
 For the directives ErrorLog and CustomLog, the log files do not need  to contain the domain name. Here, use a name of your choice.
 ServerAdmin designates the e-mail address of the responsible person  that can be contacted if problems arise. In the event of errors, Apache  gives this address in the error messages it sends to clients.

```


```
#NameVirtualHost 127.0.0.1
#<VirtualHost 127.0.0.1>
NameVirtualHost *

<Virtualhost *>
        DocumentRoot /var/www/
        ServerName localhost

        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews +Includes
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>

<VirtualHost *>
        DocumentRoot /var/www/foto/
        ServerName foto.localhost

        <Directory /var/www/foto/>
                Options Indexes FollowSymLinks MultiViews +Includes
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>

<Virtualhost *>
        DocumentRoot /var/www/ftp/
        ServerName ftp.localhost

        <Directory /var/www/ftp/>
                Options Indexes FollowSymLinks MultiViews +Includes
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>

```

---

### Post by pino262 on 2010-09-04
Ok now i have one last question: Can any1 post a clean /etc/apache2/sites-available/default file for further reference, i totally messed up mine

---

### Post by BkkBonanza on 2010-09-04
You should be able to find that file in the deb package for Apache, either in your apt-get cache files or on Launchpad. You can use dpkg to get in and find the file without re-installing.

**ls -lsa /var/cache/apt/**

**dpkg -x /var/cache/apt/the_pkg.deb tmp**

Find the file in tmp and copy to where you want. Remove tmp,

**rm -rfd tmp**

---


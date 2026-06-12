---
title: "Cannot Get Multiple Sites Working on Local Network"
date: 2008-10-14
forum: Server Platforms
---

### Post by skateoroma on 2008-10-14
I've installed Ubuntu **server** 8.04 and LAMP on one machine and set up 2 virtual hosts by following the ApacheMySQLPHP documentation on ubuntu.com.  I can browse the default site from another machine on the network, but I cannot browse the other site from within my local network.  I would like to use this setup as a development/test server before I promote code to websites I design.  The sites are hosted on a pay server and I tried to recreate the document root path on my local server.  Can anyone please help with this?  Thanks...

default
```

NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/vhosts/bovell-net.com/httpdocs/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/vhosts/bovell-net.com/httpdocs/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
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

</VirtualHost>

```

2nd Site: mahalalove.com
```

<VirtualHost *>
        ServerAdmin webmaster@localhost
        ServerName www.mahalalove.com
        ServerAlias mahalalove.com *.mahalalove.com
        DocumentRoot /var/www/vhosts/mahalalove.com/httpdocs/
</VirtualHost>

```

---

### Post by lykwydchykyn on 2008-10-15
I didn't see a "servername" directive in the first file.  I don't know if it's required but you might try adding that.

Also, how are you doing name resolution on your network?  Do both site names point to this server's IP in your DNS?

---

### Post by devonps on 2008-10-15
You should also look into updating your /etc/hosts file for each machine on your network that wants to access each site.

---

### Post by skateoroma on 2008-10-18
> **lykwydchykyn said:**
> I didn't see a "servername" directive in the first file.  I don't know if it's required but you might try adding that.

Also, how are you doing name resolution on your network?  Do both site names point to this server's IP in your DNS?

I added the servername directive to the default file and followed the instructions on ubuntu documentation site to set up DNS using BIND9, but I still cannot browse the second website from within my local network.  I'm stuck...

> **devonps said:**
> You should also look into updating your /etc/hosts file for each machine on your network that wants to access each site.

I've added the IP address of the other machine but still no luck.

Any other ideas?  Thanks again for your help.

```

NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost
        ServerName www.bovell-net.com
        ServerAlias bovell-net.com *bovell-net.com
        DocumentRoot /var/www/vhosts/bovell-net.com/httpdocs/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/vhosts/bovell-net.com/httpdocs/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

left the rest of the file out, it's displayed above.

```

---

### Post by alienprdkt on 2008-10-18
1. First create the appropriate DNS records on your DNS server to point to 
vhost1.domain.comand vhost2.domain.comto 192.168.1.100. See the 
“Configuring DNS  for a Virtual Host:
    
           -1. Create a zone file for the new domain. (See the preceding section for more on 
zone files.) 
2. In the /etc/named.conffile, add the following lines to enable the newdomain 
zone. 
zone “newdomain.com” IN { 
type master; 
file “newdomain.zone”; 
allow-update { none; }; 
}; 
This tells the named (DNS daemon) that the zone file for newdomain.comis 
/var/named/newdomain.zoneand that it is the primary (master) DNS server 
for this zone. 
3. Run the killall -HUP namedcommand to force the name server to reload 
the /etc/named.confand the new zone file. 
4. Try to ping [www.newdomain.com](www.newdomain.com). If you do not get a response, check the 
/var/log/messagesfile for any typos or other errors that name server 
(named_) might have reported in either /etc/named.confor /var/named/ 
newdomain.zonefiles. In such case, correct the typos or errors and restart 
the server as discussed in the previous step. 
5. Once you can ping the [www.newdomain.com](www.newdomain.com), you are ready to create Apache 
configuration for this virtual host as described in earlier sections of this 
chapter. 

6. Create a configuration segment similar to the following in the httpd.conffile. 
NameVirtualHost 192.168.1.100 
<VirtualHost 192.168.1.100> 
ServerName vhost1.domain.com 
ServerAdmin [email]someone@vhost1.domain.com[/email] 
DocumentRoot “/www/vhost1/htdocs” 
# 
# Any other directives you need can go here 

</VirtualHost> 
<VirtualHost 192.168.1.100> 
ServerName vhost2.domain.com 
ServerAdmin [email]someone@vhost2.domain.com[/email] 
DocumentRoot “/www/vhost2/htdocs” 
# 
# Any other directives you need can go here 
# 
</VirtualHost> 
Don’t forget to create the document root directories if you don’t have them 
already. Also, if you need to add more directives in each of the virtual host 
configuration you can do so. 
7. Restart Apache using  
#sudo /etc/init.d/apache2 restart 
command 
and access each of the virtual hosts using [http://vhost1.domain.comand](http://vhost1.domain.comand) 
[http://vhost2.domain.com](http://vhost2.domain.com).

---


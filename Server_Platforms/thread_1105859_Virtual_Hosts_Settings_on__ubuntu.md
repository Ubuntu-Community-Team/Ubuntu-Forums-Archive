---
title: "Virtual Hosts Settings on  ubuntu"
date: 2009-03-25
forum: Server Platforms
---

### Post by skip.qiu on 2009-03-25
Dear all :
   I set up a virtual host on my ubuntu , but it cann't work . my file is vhdns in the site-avalable :
NameVirtualHost 192.168.1.219
<VirtualHost www1.skip.com>
        ServerAdmin webmaster@localhost
        ServerName www1.skip.com:80
        DocumentRoot /var/web5/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/web5/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
        LogLevel warn
</VirtualHost>

<VirtualHost www2.skip.com>
        ServerAdmin webmaster@localhost
        ServerName www2.skip.com:80
        DocumentRoot /var/web6/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/web6/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
        LogLevel warn
</VirtualHost>

I have add the list to the dns : www1 IN A 192.168.1.219  AND  WWW IN A 192.168.1.219  
the dns is ok , I use nslookup have checked it , when I run "service apache2 restart" . It appears :
 root@ubuntu:/etc/apache2/sites-available# service apache2 restart
 * Restarting web server apache2                                                               [Wed Mar 25 00:21:57 2009] [error] (EAI 5)No address associated with hostname: Could not resolve host name www1.skip.com -- ignoring!
[Wed Mar 25 00:21:57 2009] [error] (EAI 5)No address associated with hostname: Could not resolve host name www2.skip.com -- ignoring!
[Wed Mar 25 00:21:57 2009] [error] VirtualHost 192.168.1.219:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
 ... waiting [Wed Mar 25 00:21:58 2009] [error] (EAI 5)No address associated with hostname: Could not resolve host name www1.skip.com -- ignoring!
[Wed Mar 25 00:21:58 2009] [error] (EAI 5)No address associated with hostname: Could not resolve host name www2.skip.com -- ignoring!
[Wed Mar 25 00:21:58 2009] [error] VirtualHost 192.168.1.219:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
                                                                                        [ OK ]



anyone can help me 
many thanks .
skip

---

### Post by lucaspr on 2009-03-25
How is your DNS configured? 

Apache claims it can't resolve www1 and www2 so something must be wrong with your DNS.

Do you run bind9 or something else? Some more info about your DNS would be helpfull.

---

### Post by BkkBonanza on 2009-03-25
Can you check your syntax on the <VirtualHost ...> lines. I don't think that's right off the top of my head. I think it needs either * or an ip value there, not a name.

ServerName tells Apache the name. I think VirtualHost tells it what ip:port to listen on. I don't know if you can put the port on the ServerName line either.

Also you can run apache with syntax checking and it will check your file without trying to start. Check the manual for that. In fact, just read the docs on apache.org for all this.

[http://httpd.apache.org/docs/2.2/mod/core.html#virtualhost](http://httpd.apache.org/docs/2.2/mod/core.html#virtualhost)

Unless you have several IPs assigned to your machine yu should just use * and it will use whatever. That way if you change your ip then you don't have to go editing things everywhere. Also port 80 is default and need not be specified.

---

### Post by skip.qiu on 2009-03-25
thank you for your quick response , my dns file is db.skip.com:
$TTL    604800
@       IN      SOA     skip.com.       root.skip.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@        IN     NS      ns.skip.com.
@        IN     A       192.168.1.222
ns       IN     A       192.168.1.222
www      IN     A       192.168.1.98
www1     IN     A       192.168.1.219
www2     IN     A       192.168.1.219
the file /etc/bind9/db.192 is :
;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA     skip.com.       root.skip.com. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.
222     IN      PTR     ns.skip.com.
98      IN      PTR     [www.skip.com](www.skip.com).
219     IN      PTR     mail.slip.com.
219     IN      PTR     mail.skip.com.


I set a windows OS's dns to 192.168.1.222(the dns on unbuntu) I use the nslookup on the windows, the dns can work .I input www1.skip.com , it appear 192.168.1.219.

---

### Post by skip.qiu on 2009-03-25
BkkBonaza , thank you for your help . I'm sorry I'm not very clear about your idea . I changed the file like this  :
<VirtualHost www1.skip.com>
        ServerAdmin webmaster@localhost
        ServerName www1.skip.com
        DocumentRoot /var/web5/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/web5/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
        LogLevel warn
</VirtualHost>

<VirtualHost www2.skip.com>
        ServerAdmin webmaster@localhost
        ServerName www2.skip.com
        DocumentRoot /var/web6/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/web6/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
        LogLevel warn
</VirtualHost>

when I restart the apache2 ,it appears :root@ubuntu:~# service apache2 restart
 * Restarting web server apache2                                                 [Wed Mar 25 18:04:55 2009] [error] (EAI 5)No address associated with hostname: Could not resolve host name www1.skip.com -- ignoring!
[Wed Mar 25 18:04:55 2009] [error] (EAI 5)No address associated with hostname: Could not resolve host name www2.skip.com -- ignoring!
 ... waiting [Wed Mar 25 18:04:56 2009] [error] (EAI 5)No address associated with hostname: Could not resolve host name www1.skip.com -- ignoring!
[Wed Mar 25 18:04:56 2009] [error] (EAI 5)No address associated with hostname: Could not resolve host name www2.skip.com -- ignoring!
                                                                          [ OK ]


add :I set other virtualhost on the ubuntu like this :
 <VirtualHost 192.168.1.222:80>
        ServerAdmin webmaster@localhost
        ServerName 192.168.1.222:80
        DocumentRoot /var/web3/
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
        LogLevel warn
</VirtualHost>

yes , there are two ips on the ubuntu 192.168.1.219 and 192.168.1.222.
now i don't now how to do fix it .   
many thanks 
cheers 
skip

---

### Post by BkkBonanza on 2009-03-26
I'm really unclear what you want to end up with. Did you read that doc link? 
It seems you have both www1 and www2 on the same ip according to your dns output. If you want them on different ips then below is wrong.

Try like this,

NameVirtualHost *:80

<VirtualHost 192.168.1.219>
ServerAdmin webmaster@localhost
ServerName www1.skip.com
DocumentRoot /var/web5/
</VirtualHost>


<VirtualHost 192.168.1.219>
ServerAdmin webmaster@localhost
ServerName www2.skip.com
DocumentRoot /var/web6/
</VirtualHost>

You can put different ips in there but then you need to set your dns to route the names to the correct ips you set here.

---

### Post by skip.qiu on 2009-03-26
I'm sorry, maybe I hvae not spoke it clearly . I just want to set up a virtual host,which use the same ipaddress ,the same port ,but the different domains. they are www1.skip.com and www2.skip.com  . 
now I try your mind , it appears :
root@ubuntu:/etc/apache2/sites-available# service apache2 restart
 * Restarting web server apache2                                                 [Wed Mar 25 22:22:10 2009] [warn] VirtualHost 192.168.1.219:0 overlaps with VirtualHost 192.168.1.219:0, the first has precedence, perhaps you need a NameVirtualHost directive
[Wed Mar 25 22:22:10 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
 ... waiting [Wed Mar 25 22:22:12 2009] [warn] VirtualHost 192.168.1.219:0 overlaps with VirtualHost 192.168.1.219:0, the first has precedence, perhaps you need a NameVirtualHost directive
[Wed Mar 25 22:22:12 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
                                                                          [ OK ]
I don't why ,and I'v no idea .
thank you very much. 
cheers

---

### Post by BkkBonanza on 2009-03-26
Ok. It's more clear now. You want them both on one ip. This should work.
You just use one section. My apache is a bit rough now as I've been using nginx for a year and just going by memory now...
You don't need the ip based VirtualHost sections.

NameVirtualHost *:80

ServerAdmin webmaster@localhost
ServerName www1.skip.com
DocumentRoot /var/web5/

ServerAdmin webmaster@localhost
ServerName www2.skip.com
DocumentRoot /var/web6/

---

### Post by skip.qiu on 2009-03-28
I'm sorry to delay , because of the bad internet here yesterday.  
Thank you for your help.  According to your mind , I made it . 
my file is like this :
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName www1.skip.com
        DocumentRoot /var/web5/
        SSLEngine on
#this line is can't work , just remove this line , I don't know why?
#       SSLOptions +FakeBasicAuth +ExportCertData +CompatEnvVars +StrictRequire
        SSLCertificateFile /etc/ssl/certs/server.crt
        SSLCertificateKeyFile /etc/ssl/private/server.key

        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/web5/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
        LogLevel warn
</VirtualHost>
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName www2.skip.com
        DocumentRoot /var/web6/
        SSLEngine on
#this line is can't work , just remove this line , I don't know why?
#       SSLOptions +FakeBasicAuth +ExportCertData +CompatEnvVars +StrictRequire
        SSLCertificateFile /etc/ssl/certs/server.crt
        SSLCertificateKeyFile /etc/ssl/private/server.key

        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/web6/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
        LogLevel warn
</VirtualHost>

But there is still a small problem , I don't know what  mean this line is  ( # SSLOptions +FakeBasicAuth +ExportCertData +CompatEnvVars +StrictRequire)  I have to  add a "#" in front of it ,because it appears wrong information after adding  this line.  yeah ,I want to try to set up the ssl web .

---


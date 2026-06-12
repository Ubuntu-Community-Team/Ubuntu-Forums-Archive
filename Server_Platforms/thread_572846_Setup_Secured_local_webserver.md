---
title: "Setup Secured local webserver"
date: 2007-10-10
forum: Server Platforms
---

### Post by rockymaxsource on 2007-10-10
Hey All,

I'm using Ubuntu 7.04

I enabled the ssl module for apache2, created a key by "openssl genrsa -des3 -out server.key 1024" and use "openssl req -new -key server.key -out server.csr" to created a CSR. Afterwards created a self signed certificate by "openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.crt". Then Installed the certificate by "sudo cp server.crt /etc/ssl/certs and sudo cp server.key /etc/ssl/private". I pasted the below lines in the VirtualHost directive for [www.testdomain.in](www.testdomain.in) under the DocumentRoot line:
"SSLEngine on

SSLOptions +FakeBasicAuth +ExportCertData +CompatEnvVars +StrictRequire

SSLCertificateFile /etc/ssl/certs/server.crt
SSLCertificateKeyFile /etc/ssl/private/server.key"

I also put Listen 443 in apache2.conf file. I can reload the apache but [https://testdomain.in](https://testdomain.in) gives me the below error:"
The connection was interrupted   

The connection to [www.etsjets1.in](www.etsjets1.in) was interrupted while the page was loading."

Can any of you give some hint on how to solve this please?

Blessings,
Rockky

---

### Post by James79 on 2007-10-10
Is this a local server on your private lan? If so, what happens if you access directly by IP? 

ie [https://192.168.0.10](https://192.168.0.10)

---

### Post by rockymaxsource on 2007-10-11
Hey James79,

Yes it is a local server. [https://192.168.1.19](https://192.168.1.19) gives me the same error.

Blessings,
Rocky

---

### Post by twistedtwig on 2007-10-11
probably completely nothing to do with it but is the port open on the server?  nmap it from your lan, there are also free online nmap scans available to make sure 443 is open to the world.

apart from that sorry never seen that issue before

---

### Post by MJN on 2007-10-11
It sounds like you're making a connection... Post the output of the following:

```
openssl s_client localhost:443
```Whilst connected, type **GET** to see if your default page is downloaded.

Edit: Also post your Apache config - you do have an SSL virtual host taking requests on :443? (I don't just mean the Listen statement but rather a <Virtualhost *:443> directive, or similar).

Mathew

---

### Post by conjur3r on 2007-10-11
What do the apache error logs say?

---

### Post by thynk on 2007-10-11
Interesting!  I'm seeing the same thing, on a production site we're trying to install SSL on one of the virutual hosts.  on the local box, 

openssl s_client -connect localhost:443

returns SSL cert info and GET downloads the page.  on the local system, [https://localhost](https://localhost) works!

However, on a remote system... 

openssl s_client -connect ssl.site.com:443
CONNECTED(00000003)
7546:error:140770FC:SSL routines:SSL23_GET_SERVER_HELLO:unknown protocol:s23_clnt.c:567:

and [https://ssl.site.com](https://ssl.site.com) remote gives the The connection to ssl.site.com  was interrupted while the page was loading.

Suggestions?

---

### Post by MJN on 2007-10-11
Again, post your config so we can maybe see what's up. We're flying blind without it...

Mathew

---

### Post by thynk on 2007-10-12
> **MJN said:**
> Again, post your config so we can maybe see what's up. We're flying blind without it...

Mathew

Okay, fair enough :-) I'm clearly not an apache2 guru especially with virtual hosts.  The below works for SSL, but breaks all the other non-ssl virtual hosts.  If we set it up to work for the normal virtual hosts, ssl fails.  We followed this thread to get this far... [http://ubuntuforums.org/showthread.php?t=560608&highlight=apache2+ssl](http://ubuntuforums.org/showthread.php?t=560608&highlight=apache2+ssl)

On restart we get the following errors
```
[Thu Oct 11 22:56:14 2007] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Thu Oct 11 22:56:14 2007] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Thu Oct 11 22:56:14 2007] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Thu Oct 11 22:56:14 2007] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Thu Oct 11 22:56:14 2007] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Thu Oct 11 22:56:14 2007] [warn] NameVirtualHost *:443 has no VirtualHosts
[Thu Oct 11 22:56:14 2007] [warn] NameVirtualHost *:80 has no VirtualHosts
```

the SSL virtual host is defined as

```
NameVirtualHost *:443
<VirtualHost *:443>
  SSLEngine On
  SSLOptions +FakeBasicAuth +ExportCertDAta +StrictRequire
  SSLCertificateFile /etc/apache2/ssl/store.ssl.com.crt
  SSLCertificateKeyFile /etc/apache2/ssl/store.ssl.com.key
  SSLCertificateChainFile /etc/apache2/ssl/store.ssl.com.key
  ServerName store.ssl.com
  DocumentRoot /var/www/store.ssl.com
</VirtualHost>
```

the default is defined as 
```
NameVirtualHost *:80
<VirtualHost *:80>
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

and as an example the one of the non ssl sites
```
<VirtualHost *>
  ServerName www.nonssl.com
  ServerAlias nonssl.com
  DocumentRoot /var/www/www.nonssl.com
</VirtualHost>
```

---

### Post by rockymaxsource on 2007-10-12
Hey MJN,

Thank you very much for your reply! 
> lover@woody:~/Desktop$ sudo openssl s_client -host localhost -port 443 gives me the below error:
> CONNECTED(00000003)
12982:error:140770FC:SSL routines:SSL23_GET_SERVER_HELLO:unknown protocol:s23_clnt.c:567:


The /etc/apache2/apache2.conf the virtual host section has the below defination:
> <VirtualHost *:443>
ServerName [www.etsjets1.in](www.etsjets1.in)
ServerAlias etsjets1.in *.etsjets1.in
DocumentRoot /home/lover/public_html/etsjets1

SSLEngine on
SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire
SSLCertificateFile /etc/ssl/certs/server.crt
SSLCertificateKeyFile /etc/ssl/private/server.key
<Directory /home/lover/public_html/etsjets1>
#Options Indexes FollowSymLinks
AllowOverride All
</Directory>
</VirtualHost>


Blessings,
Rocky

---

### Post by MJN on 2007-10-12
Guys, this could get seriously confusing diagnosing two faults in tandem!

However, there's every chance the cause is the same so let's carry on...

Both of you try adding the suffix **:443** to your servername entries (e.g servername [www.example.com:443]("http://www.example.com:443")) as this should enforce stricter matching of virtual hosts to incoming requests. I think the problem at the moment is that your HTTPS requests are being responded to by your non-HTTP configurations.

Mathew

P.S. 'Thynk' - it sounds like you may have duplicated your Namevirtualhost *:80 (and 443) directives - they should only be appearing once in your entire config (put them in apache2.conf as it sounds like you've got multiple sites in sites-available). Also, it sounds like you're using different files for each site - you have enabled each one with **a2enmod **?

P.P.S. I take it both of you have only got **one** SSL site/section config - _across your entire site_? You can only have one SSL site per IP address so having two matching sections will cause problems (the first will usually be used).

P.P.P.S. Both of you also try setting your SSL virtualhost directive to <Virtualhost _default_:443> - this will enforce that site to be used as the 'default' in the case of a non-matched IP address (instead of using the default site config, which is not SSL-enabled).

---


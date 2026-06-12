---
title: "Virtual Host - Domain name issue"
date: 2021-01-08
forum: Server Platforms
---

### Post by samuli-latvala on 2021-01-08
Hello


I have issue with my web server and virtual host.
When using domain name [http://www.ets2kb.co](http://www.ets2kb.co) it jumps on right folder but for some reason on address bar, ip address is now visible instead domain name.


I have disabled default 000-conf and using
My /etc/apache2/sites-available/ets2kb.co.conf


```
<VirtualHost 127.0.0.1:80 192.168.0.2:80 84.10.187.148:80 [fe80::ff05:a698:5fa2:7956]:80>

ServerName ets2kb.co
ServerAlias www.ets2kb.co
DocumentRoot /var/www/html/forum


        <Directory /var/www/html/forum>
            Options FollowSymLinks
            AllowOverride All
            Require all granted
        </Directory>


ErrorLog ${APACHE_LOG_DIR}/ets2kb.co_error.log
CustomLog ${APACHE_LOG_DIR}/ets2kb.co_access.log combined
</VirtualHost>
```


And hosts file:
```
127.0.0.1       localhost ets2kb.co www.ets2kb.co
::1             localhost ip6-localhost ip6-loopback
ff02::1         ip6-allnodes
ff02::2         ip6-allrouters
192.168.0.2     localhost
127.0.1.1       ets2kb.co www.ets2kb.co
84.10.187.148   ets2kb.co www.ets2kb.co
184.168.131.241 ets2kb.co www.ets2kb.co
```


Any ideas?

---

### Post by TheFu on 2021-01-08
a) Don't put IP addresses into the .conf file.  Use something like this:
```
   <VirtualHost *:80>
```

b) Set the servername correctly it must be on a separate line:
```
     ServerName [www.ets2kb.co](www.ets2kb.co)
```

c) For a webapp, you may need to setup an alias too:
```
     Alias [www.ets2kb.co](www.ets2kb.co)  /var/www/html/forum
```

Those are my guesses.  Most forums will have detailed examples of config files.  Also, you need to create a symlink from the sites-available/ directory into the sites-enabled/ directory for the file, then reload or restart apache.

Also, if you aren't using Apache (you don't actually say), then other web servers have slightly different config needs and don't look in the /etc/apache* dirs.  Some of those other web servers require ';' at the end of most lines too.

Does your host actually have those exact IP addresses assigned directly, not the upstream router?

---

### Post by samuli-latvala on 2021-01-08
Yes, it is quite standard LAMP setup and I have reverted my conf's back to near 'original'. Symlinks, boots etc done (it is forwarding to folder after all). 


/ets/hosts
```
127.0.0.1       localhost
::1             localhost ip6-localhost ip6-loopback
ff02::1         ip6-allnodes
ff02::2         ip6-allrouters
192.168.0.2     ets2kb.co
```




/etc/apache2/sites-available/ets2kb.co.conf
```
<VirtualHost *:80>
        ServerName www.ets2kb.co
        ServerAlias www.ets2kb.co
        Alias www.ets2kb.co  /var/www/html/forum
        DocumentRoot /var/www/html/forum


        <Directory /var/www/html/forum>
            Options FollowSymLinks
            AllowOverride All
            Require all granted
        </Directory>


ErrorLog ${APACHE_LOG_DIR}/ets2kb.co_error.log
CustomLog ${APACHE_LOG_DIR}/ets2kb.co_access.log combined
</VirtualHost>

```






Issue still persists.

---

### Post by TheFu on 2021-01-08
LAMP configs need much more setup.  For a static website, the stuff above should be sufficient.
I don't use Apache much here.  For a static website on nginx, it is just 6 lines in the site-config. I use a few more for log formatting, but that's it.

For a LAMP config, usually all sorts of rewrite rules are needed to hide the .php at the end of every target, protect against attackers, prevent people from using upload areas on my server for their own needs, etc.  Someone else will have to help with that.  I'm not confident enough to put any LAMP webapp onto the internet.  Mine are all internal-use only - access from the internet requires a VPN connection first.

---

### Post by SeijiSensei on 2021-01-08
> **samuli-latvala said:**
> Hello
I have issue with my web server and virtual host.
When using domain name [http://www.ets2kb.co](http://www.ets2kb.co) it jumps on right folder but for some reason on address bar, ip address is now visible instead domain name.

What the heck is address 84.10.187.148, and why is it in use?  If I lookup [www.ets2kb.co](www.ets2kb.co), it points to 184.168.131.241. Just use one address and stick to it. Also make sure reverse DNS lookups are set up properly so that 184.168.131.241 points to "www.ets2kb.com" instead of 
"ip-184-168-131-241.ip.secureserver.net" as it does now?

I've written in PHP for over two decades. I never obfuscate the ".php" in my script names, nor do any of the major PHP-based systems like WordPress, nor indeed this very forum. I've never had a site compromised by using PHP or displaying scripts with ".php" extensions.  As far as I can tell, PHP sites are no less secure than ones written in Python or Perl as long as the author takes the usual steps to sanitize user input and the like.

---

### Post by samuli-latvala on 2021-01-08
> **SeijiSensei said:**
> What the heck is "address bar?"[COLOR=#FFFFFF][FONT=&amp]
fdasd
[IMG]https://i.imgur.com/Gq9FmZq.png[/IMG][/FONT][/COLOR]

---

### Post by samuli-latvala on 2021-01-08
> [COLOR=#000000]Just to clarify things, your local host file on your server does NOT need to know the domain name or have it match what others see it as. You could have your FQDN setup on your internal DNS to return the internal IP for your LAN PCs but everyone outside would see your FQDN as the IP on your firewall.[/COLOR]

[COLOR=#000000]Apache does not care what the server actually "pings" the FQDN as...it does care what the inbound URL is...regardless if the inbound connection is coming from the WAN or LAN / VPN.[/COLOR]

[COLOR=#000000]Simplistic Example #1: A PC puts this in the URL of the web browser: [/COLOR][http://www.ets2kb.co]("http://www.ets2kb.co/")[COLOR=#000000] and by whatever means (Internet DNS, Local DNS, Local host entry) it reaches the Apache server. The server will see "www.ets2kb.co" in the inbound URL and look for all enabled sites that have a matching "ServerName" for "www.ets2kb.co" and proceed to use that configuration.[/COLOR]

[COLOR=#000000]Simplistic Example #2: A PC puts this in the URL of the web browser: [/COLOR][http://84.10.187.148]("http://84.10.187.148/")[COLOR=#000000] which means it directly connects to your firewall and is routed to the Apache server. The server will see "84.10.187.148" in the inbound URL and look for all enabled sites that have a matching "ServerName" for "84.10.187.148" and proceed to use that configuration. If it finds no match, it will use the 1st site it finds (typically the default but if ets2kb is the only site enabled, it should use it...but will not correct the URL on the web browser unless you have a re-direct in the config.[/COLOR]

[COLOR=#000000]You can verify what is enabled with this command...which shows the link and where it is linked to (in the sites-available):[/COLOR]
[COLOR=#000000]Code:
ls -l /etc/apache2/sites-enabled/[/COLOR]
[COLOR=#000000]LHammonds[/COLOR]

I got this:

```
pi@ets2kb:~ $ ls -l /etc/apache2/sites-enabled/
total 0
lrwxrwxrwx 1 root root 33 Jan  8 13:12 ets2kb.co.conf -> ../sites-available/ets2kb.co.conf

```

Checking now from my domain provider if I have missed something.

---


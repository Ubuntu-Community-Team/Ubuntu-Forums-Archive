---
title: "Reverse Proxy Clarification"
date: 2016-04-01
forum: Server Platforms
---

### Post by Roasted on 2016-04-01
Hello friends. I'm trying to accomplish the goal of binding two boxes to one IP address. We all know this isn't possible, but it seems as if a reverse proxy is the ticket. I looked through a multitude of guides, but I'm finding a large portion of these guides to leave me with some questions. Most guides are for nginx, which doesn't help me much given I'm using apache. Most of what I see is a little vague in certain areas, and the guides in question often differ in their approach (which doesn't exactly clarify things).

To lay out a few details, I have two servers running at my house. One is for basic web stuff + ownCloud + IRC etc. The other is running ZoneMinder and NAS-related uses, which I'd like to access externally to get into the web interface of ZM. Both servers are Ubuntu Server 14.04.

Let's refer to these details (mostly so I can stay sane):
ownCloud/main web server = "web server" = 192.168.1.22
ZoneMinder/NAS box = "ZM server" = 192.168.1.20
Lastly, let's say my domain is myhomedomain.org

The goal is to have myhomedomain.org hit the web server, but I want to have a different URL to access the ZM box, such as zm.myhomedomain.org or myhomedomain.org/zm. Either works.

Another potential snafu: I have apache auto redirecting all http traffic as https, so if you hit [http://myhomedomain.org](http://myhomedomain.org) it auto pipes it to [https://myhomedomain.org](https://myhomedomain.org).

Using Digital Ocean's approach, I have all of the modules activated, but their implementation is where I get a little gray.

```
<VirtualHost *:*>
    ProxyPreserveHost On

    # Servers to proxy the connection, or;
    # List of application servers:
    # Usage:
    # ProxyPass / http://[IP Addr.]:[port]/
    # ProxyPassReverse / http://[IP Addr.]:[port]/
    # Example: 
    ProxyPass / http://0.0.0.0:8080/
    ProxyPassReverse / http://0.0.0.0:8080/

    ServerName localhost
</VirtualHost>
```

In the 0.0.0.0 examples, I assume I'm supposed to be pointing towards 192.168.1.20 (the IP of ZM), correct? In particular, the address is 192.168.1.20/zm, so I figured it would look like this (keeping in mind the guide says if you are using SSL, you are to make a secondary virtualhost, one for 80 one for 443).

```

<VirtualHost *:*>
    ProxyPreserveHost On

    # Servers to proxy the connection, or;
    # List of application servers:
    # Usage:
    # ProxyPass / http://192.168.1.20:80/zm/
    # ProxyPassReverse / http://192.168.1.20:80/zm/
    # Example:
    ProxyPass / http://192.168.1.20:80/zm/
    ProxyPassReverse / http://192.168.1.20:80/zm/

    ServerName localhost
</VirtualHost>
Listen 443

NameVirtualHost *:443
<VirtualHost *:443>

    SSLEngine On

    # Set the path to SSL certificate
    # Usage: SSLCertificateFile /path/to/cert.pem
    SSLCertificateFile /etc/apache2/ssl/myhomedomain_org.crt


    # Servers to proxy the connection, or;
    # List of application servers:
    # Usage:
    # ProxyPass / http://192.168.1.20:80/zm/
    # ProxyPassReverse / http://192.168.1.20:80/zm/
    # Example:
    ProxyPass / http://192.168.1.20:80/zm/
    ProxyPassReverse / http://192.168.1.20:80/zm/

    # Or, balance the load:
    # ProxyPass / balancer://balancer_cluster_name

</VirtualHost>


```

When restarting Apache after this change, two errors are listed:
AH00548: NameVirtualHost has no effect and will be removed in the next release /etc/apache2/sites-enabled/000-default.conf:17
(98)Address already in use: AH00072: make_sock: could not bind to address [::]:443

Overall I'm a little unsure. If anybody has any suggestions, insight, or any sort of setup guides that might help I'd *greatly* appreciate it!

---

### Post by SeijiSensei on 2016-04-01
I think you need to have two virtual hosts with different names (ServerName or ServerAlias) on the proxy gateway.  Each configuration should have a separate ProxyPass and ProxyPassReverse pointing to their respective machines.  The servers themselves also need to have virtual configurations with the same ServerName or ServerAlias specifications.

If only one of them has to be HTTPS, that is okay.  But if you want SSL on both connections that's really hard to implement.  Usually the rule is one IP per SSL server.  There are some new ways around that limitation that I haven't tried though.

---

### Post by Roasted on 2016-04-01
> **SeijiSensei said:**
> I think you need to have two virtual hosts with different names (ServerName or ServerAlias) on the proxy gateway.  Each configuration should have a separate ProxyPass and ProxyPassReverse pointing to their respective machines.  The servers themselves also need to have virtual configurations with the same ServerName or ServerAlias specifications.

If only one of them has to be HTTPS, that is okay.  But if you want SSL on both connections that's really hard to implement.  Usually the rule is one IP per SSL server.  There are some new ways around that limitation that I haven't tried though.

Is that to say that I'd have two Virtualhosts in /etc/apache2/sites-enabled/000-default.conf on the web server (192.168.1.22) with proxy pass + proxy pass reverse pointing to 192.168.1.20? 

And then on the ZM/NAS box (192.168.1.20) I'd have, for all intents and purposes, seemingly identical Virtualhosts listed except pointing to 192.168.1.22?

Also, if I'm leveraging SSL/HTTPS on the main web server that's acting as the proxy, is there any benefit to working with SSL/HTTPS on the ZM/NAS box? Or can I let that remain HTTP and still benefit from SSL/HTTPS thanks to the proxy box having it enabled?

...hope those questions made sense. Thanks for your insight!

---

### Post by SeijiSensei on 2016-04-01
Is the box running the proxy also serving as a web server?  Then you'd have one configuration file for the local webserver with its ServerName directive and a DocumentRoot pointing to the local site.  The other configuration file would have a different ServerName and the Proxy specifications pointing back to 192.168.1.22.

However, as I said, if you want to use SSL to communicate with the proxy box, then it will only be able to encrypt one connection or the other.  It sounds like you want to use HTTPS with the site on the proxy box itself, so you can put that specfication in a <VirtualHost *:443> container, and use a <VirtualHost *:80> container for the site that runs the proxy. 

You will have to choose one or the other site to protect with SSL unless you can get an IP subnet from your ISP.  Then you could assign separate IP addresses for each site and use SSL with both of them.  If you're on a residential network, this is probably not an option available to you.

---

### Post by Roasted on 2016-04-01
> **SeijiSensei said:**
> Is the box running the proxy also serving as a web server?  Then you'd have one configuration file for the local webserver with its ServerName directive and a DocumentRoot pointing to the local site.  The other configuration file would have a different ServerName and the Proxy specifications pointing back to 192.168.1.22.

However, as I said, if you want to use SSL to communicate with the proxy box, then it will only be able to encrypt one connection or the other.  It sounds like you want to use HTTPS with the site on the proxy box itself, so you can put that specfication in a <VirtualHost *:443> container, and use a <VirtualHost *:80> container for the site that runs the proxy. 

You will have to choose one or the other site to protect with SSL unless you can get an IP subnet from your ISP.  Then you could assign separate IP addresses for each site and use SSL with both of them.  If you're on a residential network, this is probably not an option available to you.

Hmm. Overall, my goal is this.

192.168.1.22, which is my main outward facing server, which serves up my DDNS, IRC, ownCloud, and a public Apache share for misc uses. This redirects http to https, so it kind of locks into using https/SSL. My router has 80 and 443 forwarded to 192.168.1.22, so once you hit myhomedomain.org, it hits the Apache config of my web (192.168.1.22) server.

What I'd like is to keep the above... yet provide an option/way/method to pull in the web interface of the 2nd box (192.168.1.20) on my LAN, which drills back to the ability to hit zm.myhomedomain.org or myhomedomain.org/zm, or something like that, and just have that particular sub-domain (if you will) pass over to the ZM/NAS box.

For example, I have a share called public on my web server, so myhomedomain.org/public brings that up from the web server. Likewise, myhomedomain.org/zm, I would like, to hit the ZM/NAS box.
i.e.:
myhomedomain.org/public = 192.168.1.22 main web server
myhomedomain.org/zm = 192.168.1.22 sees it (since it's forwarded for 80/443), realizes the /zm is on another box, and passes that connection to 192.168.1.20 to host the /zm web UI. 

I understood reverse proxy was the ticket for this. But my understanding isn't exactly extensive on building out Apache for additional uses...

---

### Post by SeijiSensei on 2016-04-01
Well, I don't think you can accomplish exactly what you want.  You would have to eliminate the redirect on the web server and use https:// URLs from outside to reach the site on that box.  You could then set up an unencrypted connection that proxies back to the ZM server.  

Alternatively you could leave the current configuration as is and bind Apache to use a different port for the proxy.  However that's just a more complicated method than simply having your router forward some high port back to the ZM machine.  Then [www.mydomain.org](www.mydomain.org) would work just as it does now, while, e.g., [www.mydomain.org:12345](www.mydomain.org:12345) would forward back to the ZM server.  You could then use SSL over both connections with this configuration if the ZM server supports that.  That's all seems a lot simpler to set up than using Apache as a proxy.

---

### Post by Roasted on 2016-04-01
This link seems to give me (in rather simple terms) that what I'm after may be accomplish-able. 

[https://docs.oseems.com/general/application/apache/configure-reverse-proxy](https://docs.oseems.com/general/application/apache/configure-reverse-proxy)

In their example they're just passing 192.168.0.10/myapp and making it available as /webapp on the main domain, which suggests that going to [www.example.com](www.example.com) hits their main web server, but going to [www.example.com/webapp](www.example.com/webapp) pipes over to 192.168.0.10/myapp.

I may have to look into this when I get access to the box, starting without SSL and from there seeing if I can enforce it somehow.

---

### Post by SeijiSensei on 2016-04-01
I really think forwarding back a high port from the router is the easiest solution.  Do you have lots of people who need to connect to the ZM server and are concerned about them not understanding a server:port type of URL?  Once you've connected the first time, you can just save the URL as a favorite in the browser.

---

### Post by Roasted on 2016-04-01
> **SeijiSensei said:**
> I really think forwarding back a high port from the router is the easiest solution.  Do you have lots of people who need to connect to the ZM server and are concerned about them not understanding a server:port type of URL?  Once you've connected the first time, you can just save the URL as a favorite in the browser.

That's not my concern. My concern is I want to do a demonstration at a local Linux LUG, but I'll need to tap into my home server for that. Port 80 or 443 is a requirement given the networking restrictions there. Couple that with the fact I think the end result is simply cleaner and there you pretty much have why I want to go this route.

Worst case, I continue leaving the ZM/NAS box inaccessible from the outside and let the web/ownCloud server do its thing. In that instance I'll just drop web/ownCloud from being forwarded to 80/443 and pop the ZM/NAS box in the 80/443 forwarded spot for this demonstration, then revert back later.

But in the end it just feels cleaner to do it the way I described above. Plus, if I do it this way, I can leverage zmNinja (Android/iOS ZoneMinder app) to tap into my camera streams. By doing this, I can remove my cameras from being individually forwarded for use with TinyCam Pro, which just makes me feel dirty since camera firmware very rarely gets updates... let alone security updates... at least in that instance they'd be sitting behind the ZM server, and ultimately, the web/ownCloud/proxy server.

---

### Post by SeijiSensei on 2016-04-01
This may not give you all the functionality you want, but you could mount the NAS share on the web server box and use an alias
```

<VirtualHost *:443>
[stuff]
Alias /myfiles /path/to/the/mounted/share
<Directory "/path/to/the/mounted/share">
     Options +Indexes
</Directory>
</VirtualHost>

```
Now [https://www.mydomain.com/myfiles/](https://www.mydomain.com/myfiles/) will display the list of files on the mounted share.  If you have more than one share to display, use multiple Alias directives.

---

### Post by Roasted on 2016-04-01
> **SeijiSensei said:**
> This may not give you all the functionality you want, but you could mount the NAS share on the web server box and use an alias
```

<VirtualHost *:443>
[stuff]
Alias /myfiles /path/to/the/mounted/share
<Directory "/path/to/the/mounted/share">
     Options +Indexes
</Directory>
</VirtualHost>

```
Now [https://www.mydomain.com/myfiles/](https://www.mydomain.com/myfiles/) will display the list of files on the mounted share.  If you have more than one share to display, use multiple Alias directives.

Unfortunately all that would do is give me a bunch of directories with thousands of images amounting to the feeds that ZoneMinder would play back automagically in the web UI seamlessly. 

What I find confusing is I've followed a ton of guides out there, but each time I can't seem to get both servers working (myhomedomain.org hitting my web server and myhomedomain.org/zm hitting the ZM/NAS box). It's either one or the other... yet my config is always set to match what I'm reading in the example guides.

I did manage to get the forwarding working (where I hit myhomedomain.org/zm and it hits the ZM/NAS box), but it works internally only. Once external, it 404's me.

I'm missing something somewhere...

---

### Post by Roasted on 2016-04-02
Woooo. Got it.

```
root@web-server:/etc/apache2/sites-available# cat 000-default.conf 
<VirtualHost *:443>
        ServerName myhomedomain.org
        ServerAdmin webmaster@localhost
        ServerAlias myhomedomain.org
	DocumentRoot /var/www/html
	SSLEngine On
	SSLCertificateFile /etc/apache2/ssl/myhomedomain_org.crt
	SSLCertificateKeyFile /etc/apache2/ssl/myhomedomain.key
	SSLCACertificateFile /etc/apache2/ssl/myhomedomain_org.ca-bundle
        ProxyPass /zm http://192.168.1.20/zm
        ProxyPassReverse /zm http://192.168.1.20/zm
</VirtualHost>	

<VirtualHost *:80>
	ServerName myhomedomain.org
	ServerAdmin webmaster@localhost
	ServerAlias myhomedomain.org
	Redirect / https://myhomedomain.org/
	DocumentRoot /var/www/html
</VirtualHost>
```

```
root@web-server:/etc/apache2/sites-available# cat default-ssl.conf 
<IfModule mod_ssl.c>
<VirtualHost _default_:443>
	ServerName myhomedomain.org
	ServerAdmin webmaster@localhost
	ServerAlias myhomedomain.org
        DocumentRoot /var/www/html
	SSLEngine On
	SSLCertificateFile /etc/apache2/ssl/myhomedomain_org.crt
	SSLCertificateKeyFile /etc/apache2/ssl/myhomedomain.key
	SSLCACertificateFile /etc/apache2/ssl/myhomedomain_org.ca-bundle
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
</IfModule>
```

This gives me everything I was aiming for. All of the web directories work and auto direct from HTTP to HTTPS, and likewise, hitting [http://myhomedomain.org/zm](http://myhomedomain.org/zm) works as well by A) switching to HTTPS automatically, and B) the fact it even works is clear indication the reverse proxy is doing its job, as the ZM/NAS box is *not* forwarded on the router in any capacity.

Huzzah!

---

### Post by SeijiSensei on 2016-04-02
Just an aside.  There is no need for a DocumentRoot directive in the HTTP Redirect stanza.  Since you're redirecting the connection, Apache just sends a 302 Redirect to the browser.  It never looks for a DocumentRoot.  You might want to add the keyword "permanent" to the Redirect statement.  Then browsers will cache the target address. By default Apache redirects are "temporary."  See: [https://httpd.apache.org/docs/current/mod/mod_alias.html#redirect](https://httpd.apache.org/docs/current/mod/mod_alias.html#redirect)

Glad you got this all figured out!

---

### Post by Roasted on 2016-04-02
> **SeijiSensei said:**
> Just an aside.  There is no need for a DocumentRoot directive in the HTTP Redirect stanza.  Since you're redirecting the connection, Apache just sends a 302 Redirect to the browser.  It never looks for a DocumentRoot.  You might want to add the keyword "permanent" to the Redirect statement.  Then browsers will cache the target address. By default Apache redirects are "temporary."  See: [https://httpd.apache.org/docs/current/mod/mod_alias.html#redirect](https://httpd.apache.org/docs/current/mod/mod_alias.html#redirect)

Glad you got this all figured out!

I just made the corresponding changes you recommended. Everything works just like before (which I of course wanted) and what you explained makes sense. Thanks for the follow up!

I hope this information helps somebody in the future. While Apache documentation is extensive, a lot of the sections certainly come across assuming you know a certain amount to plug in the gaps of their examples, as they feel limited otherwise. It's enough to get started, but requires more digging. Likewise, I found it alarming how many guides I found that looked visibly sensible yet were a number of years old and largely obsolete, making them useless for my use. Here is an edited (as per SeijiSensei's most recent recommendation) layout of my 000-default.conf and default-ssl.conf, just to help anybody else out who may dig up this thread.

A reminder this was done on Ubuntu Server 14.04.

000-default.conf:
```
root@web-server:/etc/apache2/sites-available# cat 000-default.conf 
<VirtualHost *:443>
        ServerName myhomedomain.org
        ServerAdmin webmaster@localhost
        ServerAlias myhomedomain.org
	DocumentRoot /var/www/html
	SSLEngine On
	SSLCertificateFile /etc/apache2/ssl/myhomedomain_org.crt
	SSLCertificateKeyFile /etc/apache2/ssl/myhomedomain.key
	SSLCACertificateFile /etc/apache2/ssl/myhomedomain_org.ca-bundle
        ProxyPass /zm http://192.168.1.20/zm
        ProxyPassReverse /zm http://192.168.1.20/zm
</VirtualHost>	

<VirtualHost *:80>
	ServerName myhomedomain.org
	ServerAdmin webmaster@localhost
	ServerAlias myhomedomain.org
	Redirect permanent / https://myhomedomain.org/
</VirtualHost>
```

default-ssl.conf:
```
root@web-server:/etc/apache2/sites-available# cat default-ssl.conf 
<IfModule mod_ssl.c>
<VirtualHost _default_:443>
	ServerName myhomedomain.org
	ServerAdmin webmaster@localhost
	ServerAlias myhomedomain.org
        DocumentRoot /var/www/html
	SSLEngine On
	SSLCertificateFile /etc/apache2/ssl/myhomedomain_org.crt
	SSLCertificateKeyFile /etc/apache2/ssl/myhomedomain.key
	SSLCACertificateFile /etc/apache2/ssl/myhomedomain_org.ca-bundle
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
</IfModule>
```

---


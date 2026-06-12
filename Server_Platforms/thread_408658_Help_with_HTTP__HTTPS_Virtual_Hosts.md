---
title: "Help with HTTP / HTTPS Virtual Hosts"
date: 2007-04-13
forum: Server Platforms
---

### Post by Nalum on 2007-04-13
Hey all,
I've recently set up Xampp on my Ubuntu pc and have just today set up virtual hosts. But when I got to the address I have set up I get this error page.

> 
**Bad Request**

 Your browser sent a request that this server could not understand.
Reason: You're speaking plain HTTP to an SSL-enabled server port.
Instead use the HTTPS scheme to access this URL, please.
[INDENT]Hint: [**https://www.example.com/**]("https://www.example.com/")[/INDENT]Apache/2.2.4 (Unix) DAV/2 mod_ssl/2.2.4 OpenSSL/0.9.8d PHP/5.2.1 mod_apreq2-20051231/2.5.7 mod_perl/2.0.2 Perl/v5.8.7 Server at [www.example.com]("http://www.example.com") Port 443
This is what I have in my httpd.conf file
> 
NameVirtualHost *

<VirtualHost *>
    ServerName [www.site1.nd]("http://www.site1.nd")
    DocumentRoot /opt/lampp/htdocs/site1
</VirtualHost>

<VirtualHost *>
    ServerName [www.site2.nd]("http://www.site2.nd")
    DocumentRoot /opt/lampp/htdocs/site2
</VirtualHost>

<VirtualHost *>
    ServerName [www.site3.nd]("http://www.site3.nd")
    DocumentRoot /opt/lampp/htdocs/site3
</VirtualHost>
And this is what I have in my hosts file
> 
127.0.0.1    [www.site1.nd]("http://www.site1.nd")
127.0.0.1    [www.site2.nd]("http://www.site2.nd")
127.0.0.1    [www.site3.nd]("http://www.site3.nd")
Thanks for any help you have.

---

### Post by Frosty Cold Drink on 2007-04-13
You need to fine the SSLEngine direcrive in your configuration files and set it to Off. If you want to enable SSL, check this link out, which will end up just pointing you back to another thread here, but with more info :)

[http://askcolddrink.blogspot.com/2007/03/apache-httpd-virtual-hosts-and-ssl.html](http://askcolddrink.blogspot.com/2007/03/apache-httpd-virtual-hosts-and-ssl.html)

---

### Post by Nalum on 2007-04-13
Thanks Frosty, will look at that.

---

### Post by Nalum on 2007-04-13
That site was helpful.
I changed it from what is above to this.
The bold text is the difference.
> 
NameVirtualHost ***:80**

<VirtualHost ***:80**>
    ServerName [www.site1.nd]("http://www.site1.nd/")
    DocumentRoot /opt/lampp/htdocs/site1
</VirtualHost>

<VirtualHost ***:80**>
    ServerName [www.site2.nd]("http://www.site2.nd/")
    DocumentRoot /opt/lampp/htdocs/site2
</VirtualHost>

<VirtualHost ***:80**>
    ServerName [www.site3.nd]("http://www.site3.nd/")
    DocumentRoot /opt/lampp/htdocs/site3
</VirtualHost>


---


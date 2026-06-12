---
title: "Apache as Reverse Proxy with SSL"
date: 2012-09-30
forum: Server Platforms
---

### Post by mcricker on 2012-09-30
Hi all,
 
I'm trying to set up apache as a reverse proxy. Specifically I need to expose some internal sites using https and some using http (internally they can all use http).
 
I have started with just one internal site (hosting redmine). The following config seems to work for http -
 
```
 
<VirtualHost *:80>
    ServerName redmine.DOMAIN.com
 
 
    ProxyRequests Off
    ProxyPreserveHost On
 
    ProxyPass / [http://192.168.1.14/](http://192.168.1.14/)
    ProxyPassReverse / [http://192.168.1.14/](http://192.168.1.14/)
</VirtualHost>

```
 
If I navigate to [http://redmine.DOMAIN.com](http://redmine.DOMAIN.com) then the redmine site loads. However, what I really need is to expose it as [https://redmine.DOMAIN.com](https://redmine.DOMAIN.com) which I can't seem to get working no matter what I try.
 
Does anyone know what changes I need to make to get this to work for https?
 
Thanks

---

### Post by SeijiSensei on 2012-10-01
The short answer is that the client browser will complain about a "man-in-the-middle" attack if you do this.  At a minimum, the proxy would need to have a valid server certificate for the same site as the server's own certificate.  Even then, I'm not sure if that will work.

If you have just one HTTPS site, you can simply forward port 443 back to port 443 on the server.  If you're trying to manage proxying of name-based SSL hosts, I think you'll find that very difficult to manage.  The best solution might be to use different port addresses on both the router and the server for each HTTPS site.

---

### Post by mcricker on 2012-10-01
Thanks for the reply.
 
From what I understand this should be possible with the correct ssl certs on the proxy. I have had some success whilst trying some of the examples I've found online but none of them have quite worked as I wanted.
 
I haven't tried several ssl reverse proxied sites yet but I will need to do that too. If apache cannot do this, is there another application (with an example config please!)?

---

### Post by hasan.akgoz on 2012-10-02
Hi mcricker ;
 
Can you give me output above command ?
 
1- tail -f /var/log/apache2/access.log 
2- tail -f /var/log/apache2/error.log

---

### Post by koenn on 2012-10-02
technically, apache *can* do that - what you need to do is change your vhost config to an SSL vhost (iirc there's an example in apache2/sites-available that you can adapt and  enable). 
you're going to need an SSL cert for that, specifically for the proxy's FQDN.

Then add your ReverseProxy stuff there. 

If your second leg (from the proxy to the web servers) is http, this'll work.

If the 2nd leg is https as well, you're very likely to run into the sort of trouble  SeijiSensei mentions, if only because you'll have a name mismatch between the proxy's (certified) name and the webserver's (certified) name,  which will result in a security warning.  
That is by design, because https is designed to create a secure channel between known and authenticated end points; putting a proxy in between it goes against those design goals  so it's always going to be difficult.

Afaik there is such a thing as wildcard or domain certs, but I'm not sure they'll help in a case like this. 


Depending on what you try to accomplish by using SSL, giving up on SSL on your local network might be an option (you only secure the external leg), maybe direct local traffic trough the proxy as well, ... 

It might be possible to get a solution by configuring multiple vhosts on the proxy, each proxying for 1 specific (https) web server, using the same name and server cert on both the proxy and the web server ... (I guess this is what SeijiSensei was getting at -  I also have no idea how that would turn out).

---

### Post by mcricker on 2012-10-02
Thanks for the replies. I did manage to get this working in the end, this is the config -
```

<VirtualHost *:443>
    ServerName redmine.DOMAIN.com
    SSLEngine On
    SSLProxyEngine On
    ProxyRequests Off
    ProxyPreserveHost On
    SSLCertificateFile /etc/apachekeys/redmine.DOMAIN.com.crt
    SSLCertificateKeyFile /etc/apachekeys/DOMAIN.com.key
    SSLCertificateChainFile /etc/apachekeys/sub.class1.server.ca.pem
    SSLCACertificateFile /etc/apachekeys/ca.pem
    ProxyHTMLInterp On
    ProxyHTMLExtended On
    ProxyHTMLURLMap (.*)192.168.1.14(.*) [https://redmine.DOMAIN.com$2](https://redmine.DOMAIN.com$2) [Rin]
    ProxyPass / [https://192.168.1.14/](https://192.168.1.14/)
    ProxyPassReverse / [https://192.168.1.14/](https://192.168.1.14/)
</VirtualHost>
<VirtualHost *:443>
    ServerName sharepoint.DOMAIN.com
    SSLEngine On
    SSLProxyEngine On
    ProxyRequests Off
    SSLCertificateFile /etc/apachekeys/sharepoint.DOMAIN.com.crt
    SSLCertificateKeyFile /etc/apachekeys/DOMAIN.com.key
    SSLCertificateChainFile /etc/apachekeys/sub.class1.server.ca.pem
    SSLCACertificateFile /etc/apachekeys/ca.pem
    SetOutputFilter INFLATE;proxy-html;DEFLATE;
    ProxyHTMLInterp On
    ProxyHTMLExtended On
    ProxyHTMLURLMap (.*)192.168.1.11(.*) [https://sharepoint.DOMAIN.com$2](https://sharepoint.DOMAIN.com$2) [Rin]
    ProxyPass / [http://192.168.1.11/](http://192.168.1.11/)
    ProxyPassReverse / [http://192.168.1.11/](http://192.168.1.11/)
</VirtualHost>

```
 
Cheers :)

---

### Post by mcricker on 2012-10-03
My previous configuration seems to be working for almost all cases, I have an issue with the following string which I need to be rewritten.
 
```
http:\u002f\u002f[SIZE=2]192.168[/SIZE][SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff].1.11[COLOR=#000000]
```[/COLOR][/COLOR][/SIZE][/COLOR][/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff][COLOR=#000000]any ideas?[/COLOR]
[/COLOR][/SIZE][/COLOR][/SIZE]

---


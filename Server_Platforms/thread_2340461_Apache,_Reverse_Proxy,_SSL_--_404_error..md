---
title: "Apache, Reverse Proxy, SSL -- 404 error."
date: 2016-10-18
forum: Server Platforms
---

### Post by Roasted on 2016-10-18
Hi friends. I'm trying to get a reverse proxy to work with my Bluecherry server in an effort to proxy local requests over the Bluecherry port (7001) through my main web server. Both the web server and Bluecherry server are Ubuntu Server 14.04. I've done simple reverse proxies before and didn't have issues. To test, I installed apache2 on my laptop, set the apache port to 7001, and was able to reverse proxy just fine. Something else is going on here.

On my web server I have SSL enabled/enforced (no HTTP traffic, everything redirects to 443). On the Bluecherry server there's a self-signed certificate. I question if that has something to do with this.

I'm pasting my (current) config here in an effort to see if anyone has any suggestions or ideas to try. 

```
<VirtualHost *:443>
        ServerName homedomain.org
        ServerAdmin webmaster@localhost
        ServerAlias homedomain.org
#       DocumentRoot /var/www/html
        SSLEngine On
        SSLProxyEngine On
        SSLProxyVerify none
        SSLProxyCheckPeerCN off
        SSLProxyCheckPeerName off
        SSLProxyCheckPeerExpire off
        SSLCertificateFile /etc/apache2/ssl/homedomain_org.crt
        SSLCertificateKeyFile /etc/apache2/ssl/homedomain.key
        SSLCACertificateFile /etc/apache2/ssl/homedomain_org.ca-bundle
        ProxyRequests Off
        ProxyPreserveHost Off
        ProxyPass /bluecherry https://192.168.1.25:7001/
        ProxyPassReverse /bluecherry https://192.168.1.25:7001/
        <Location /bluecherry>
        Order allow,deny
        Allow from all
        </Location>
</VirtualHost>

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName homedomain.org
        ServerAlias homedomain.org
        Redirect permanent / https://homedomain.org/
</VirtualHost>

```

So as you can see, VirtualHost 80 redirects everything to HTTPS. This works well and has for a long time. There's just something about trying to get my web server talking to the Bluecherry server hanging this up. Again, I put apache2 on this laptop and had no issues with my reverse proxy. It routed to the basic apache install of my laptop just fine.

As you can see, I have a series of SSLProxyCert related lines. I stumbled across these when trying to troubleshoot, as some folks indicated that the fact it's a self-signed cert may be why it's fouling out. 

I'd like to, of course, keep my signed certificate on my web server intact, but I'd also like to keep the self-signed cert intact on the Bluecherry server as well (if at all possible).

Anyway, any ideas? I'd appreciate any suggestions!

---

### Post by SeijiSensei on 2016-10-19
I think this kind of setup might raise "man-in-the-middle" problems with SSL.  Why don't you just forward port 443 back to the server with iptables?  We use this method to send SSL connections from external hosts to my client's Exchange server.

```
/sbin/iptables -t nat -A PREROUTING -d ext.ip.of.router -p tcp -m tcp --dport 443 -j DNAT --to-destination ip.of.destination.server:443 
```

---

### Post by Roasted on 2016-10-19
Hmm, if it raises concerns I wonder how others do it? Surely folks/businesses out there are running a reverse proxy server which bounces users to other servers on the back end without the visitor even knowing that a transaction happened. I would surmise that anything internal that's part of the proxy (server 2, server 3, etc) would still be encrypted via the SSL auth on the front end proxy server, no? On that note, wouldn't having an internal-only server (server 2, server 3, etc) that's part of the proxy containing their own SSL cert (CA, self signed, or otherwise) only act as a benefit, no matter how slight, over the destination servers having nothing?

---

### Post by SeijiSensei on 2016-10-19
It might be possible to do this with a "wildcard" SSL certificate that matches *.domain.name.  Then it would be authoritative for both the front-end server and the ones behind it.  Just a guess though.

[Squid]("http://wiki.squid-cache.org/ConfigExamples/Intercept/SslBumpExplicit") has code to permit SSL connections through a proxy.  The proxy has a certificate that is accepted by the clients behind it and lies about the identity of the upstream site.  It's possible to use Squid as an inbound proxy, but I've never done that.

---

### Post by Roasted on 2016-10-19
Maybe the best course of action would be disabling SSL on the internal box. That would suggest, if my understanding is correct, that anything entering/leaving the actual network would be passed over SSL via the web server with its CA signed cert, but connectivity internally between the web server and the Bluecherry server would be HTTP based traffic.

Or do you believe that, despite being an internal handshake, would increase risk too much?

---

### Post by SeijiSensei on 2016-10-19
That sounds like a reasonable solution.  I'd try it out and see whether you get any sort of certificate error on the client.

I don't see any way for someone to eavesdrop on the traffic since only the segment within your local network would be unencrypted.

---


---
title: "Apache2, SSL, vhost and reverseproxy"
date: 2007-11-08
forum: Server Platforms
---

### Post by awreneau on 2007-11-08
I have a similar situation to this thread [http://ubuntuforums.org/showthread.php?t=605064&highlight=apache+ssl&page=2]("http://ubuntuforums.org/showthread.php?t=605064&highlight=apache+ssl&page=2")

But I'm throwing a twist into it. 

I'm trying to use Apache mod_proxy to connect to a 40bit server.  

Running 6.0.6 LTS
Apache/2.0.55
libapche-mod-proxy-html

modules enabled:
cgid.conf
cgid.load
proxy.conf
proxy_html.load
proxy.load
ssl.conf
userdir.conf
userdir.load

the ssl virtual host is as follows:
NamevirtualHost *:443

<VirtualHost *:443>

        # This secures the server from becoming a third party server
        ProxyRequests Off

        # Allows the proxying of a SSL connection
        ProxyVia On

        DocumentRoot /var/www/ssl

        ServerName test.local:443

        SSLProxyEngine On
        SSLCertificateFile /etc/apache2/ssl/apache.pem
#       SSLCertificateKeyFile /etc/apache2/ssl/apache.pem

        ProxyPass /ssl [https://sitewith40bitencryption/](https://sitewith40bitencryption/)
        ProxyPassReverse /ssl [https://sitewith40bitencryption/](https://sitewith40bitencryption/)

</VirtualHost>



ports.conf
Listen 80
Listen 443

created a pem w/ the following

sudo apache2-ssl-certificate -days 365

The error in /var/log/apache2/error.log reads as
[Thu Nov 08 15:33:08 2007] [error] [client 172.23.41.92] Invalid method in request \x16\x03\x01

Youre probably asking why am I proxying a 40 bit site, I asked the same question when given the task, it's a legacy app that browsers choke on and we have to have access to it.  

libxml2 is also installed


I'd really appreciate some help on this.  

Thanks

WR

---


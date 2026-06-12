---
title: "[Apache + mod_proxy] access log shows my server is being used as a proxy"
date: 2009-06-30
forum: Security
---

### Post by Ti_Uhl on 2009-06-30
My apache access log keeps getting filled up with GET request from an external ip and I can't seem to configure it correctly to block these requests. 

```
server.example.com:80 61.139.105.162 - - [30/Jun/2009:21:55:20 +0200] "GET http://ad.yieldmanager.com/imp?z=10&s=431934&u=http%3A%2F%2Fwww.myflashhome.com%2Findex.html 
HTTP/1.0" 404 342 "http://www.myflashhome.com/index.html" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.0.2) Gecko/2008091620 Firefox/3.0.2"
```I'm trying to configure mod_proxy to proxy request to other servers in my local network But I think something is misconfigured. 

```
<IfModule mod_proxy.c>
        #turning ProxyRequests on and allowing proxying from all may allow
        #spammers to use your proxy to send email.

        ProxyRequests Off

        <Proxy *>
                AddDefaultCharset off
                Order deny,allow
                Deny from all
        </Proxy>

        # Enable/disable the handling of HTTP/1.1 "Via:" headers.
        # ("Full" adds the server version; "Block" removes all outgoing Via: headers)
        # Set to one of: Off | On | Full | Block

        ProxyVia Off
</IfModule>
```and my site config file looks like this : 

```
<VirtualHost *:8080>
        ServerName test.sample.com

        RewriteEngine On
        ProxyPass / http://127.0.0.1:8001/
        ProxyPassReverse / http://127.0.0.1:8001/
</VirtualHost>

```my ports.conf looks like this  :

```
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default

#NameVirtualHost *:80
#Listen 80

Listen 8080
NameVirtualHost *:8080


<IfModule mod_ssl.c>
    # SSL name based virtual hosts are not yet supported, therefore no
    # NameVirtualHost statement here
    Listen 443
</IfModule>

```I'm really running out off option and haven't got a clue what to do. The server isn't even configured to listen on port 80 but it keeps receiving connections.....

---

### Post by bodhi.zazen on 2009-07-03
I see you have not comments :(

I would just like to ask why you are configuring a proxy to listen on port 80 and direct back to localhost:8080 ?

Why not just configure apache to listen on 8080 and skip the proxy ?

---


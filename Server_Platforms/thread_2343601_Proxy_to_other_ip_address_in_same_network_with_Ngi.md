---
title: "Proxy to other ip address in same network with Nginx?"
date: 2016-11-17
forum: Server Platforms
---

### Post by sebastiaan5 on 2016-11-17
Hello,

I'm setting up a home network with different servers but I'm kinda stuck in a problem. My set up is like this (all physical servers):

```

                                            _____Windows Server(192.168.0.3)
                                           /
Router -> Ubuntu Server(192.168.0.2) --------------FreeNas server(192.168.0.250)
                                           \_____
                                                    Ubuntu Core server(192.168.0.5)


```

So everything will go via my Ubuntu Server, The windows server is used as remote desktop and I tunnel it trough ssh (Ubuntu server).

Now what I want is when I type in my browser the external ip address for my router which is connected to port 80 of my Ubuntu server with something extra fe. https://<externalip>/bsd/ that I will be redirected to my FreeNas server.

What I tried but did not work:

nginx config:

```


#REVERSE BSD
        location \ /sevaho/bsd/ {
proxy_bind 192.168.0.250;
proxy_pass http://192.168.0.250;
}

#OTHER TEST
         location ~ /sevaho/bsd1.* {
         rewrite (/projects)$ / break;
         rewrite /projects/(.*) /$1 break;
         proxy_pass http://192.168.0.250;
         proxy_redirect / /projects/;
         proxy_set_header Host $host;
         proxy_set_header Origin http://$host;
         proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
         proxy_http_version 1.1;
         proxy_set_header Upgrade $http_upgrade;
         proxy_set_header Connection $http_connection;
         }




```

Greetings

---

### Post by TheFu on 2016-11-17
Try this:
```
upstream sevaho.example.com {
        server 10.10.10.4:8181;
}
server {
   listen   80;
   server_name  sevaho.example.com;
   access_log  /var/log/nginx/sevaho.access.log;
   error_log  /var/log/nginx/sevaho.error.log;
   server_tokens off;
   add_header X-Frame-Options SAMEORIGIN;
   add_header X-Content-Type-Options nosniff;
   add_header X-XSS-Protection "1; mode=block";
   
   location / {
                proxy_set_header  X-Real-IP  $remote_addr;
                proxy_set_header  X-Forwarded-For $proxy_add_x_forwarded_for;
                proxy_set_header  Host $http_host;
                try_files index.shtml index.html @sevaho.example.com;
    }           
                
        location @sevaho.example.com {
                proxy_pass [http://sevaho.example.com;](http://sevaho.example.com;)
        }
}

```
BTW, this works for a live site.  10.10.10.4 is the real web server on the LAN. All traffic to sevaho.example.com is proxied there. I only replaced the domain and the hostname from the real config file in my /etc/nginx/sites-available/ directory.

For SSL, how to do it depends on where the SSL termination point is.  If on the proxy server and NOT the upstream server, add the following to the "server" stanza, not the location.
```

   ssl on;
   ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
   ssl_prefer_server_ciphers on;
   ssl_ciphers "EECDH+ECDSA+AESGCM EECDH+aRSA+AESGCM EECDH+ECDSA+SHA384 EECDH+ECDSA+SHA256 EECDH+aRSA+SHA384 EECDH+aRSA+SHA256 EECDH+aRSA+RC4 EECDH EDH+aRSA RC4 !aNULL !eNULL !LOW !3DES !MD5 !EXP !PSK !SRP !DSS !MEDIUM";

   ssl_dhparam dh4096.pem;
   ssl_session_cache shared:SSL:10m;
 
   ssl_certificate     /etc/nginx/ssl/commercial_ca.crt;
   ssl_certificate_key /etc/nginx/ssl/ssl.example.com-NOPASS.key;
```
Be certain to generate a dh4096 key and make the ssl-cert.key without a password.  I haven't switched to Let's Encrypt certs on nginx yet, but that is in the plan shortly.  With apache2 as the SSL termination point, Let's encrypt setup is pretty bonehead.

Need more details? [https://www.nginx.com/resources/admin-guide/reverse-proxy/](https://www.nginx.com/resources/admin-guide/reverse-proxy/)

I wouldn't redirect to a FreeNAS box.  I'd use ssh-based access to storage. That would be sshfs, sftp, scp - there are clients for every networked OS and you don't have to worry about bad HTTPS security (HTTPS is **not** secure, BTW).  With ssh, you can use private keys to ensure security from remote locations.

---

### Post by sebastiaan5 on 2016-11-18
I'm going to be honest with you, I don't understand it what you are saying :/

This is my nginx conf:

```

add_header X-Frame-Options SAMEORIGIN;
add_header X-Content-Type-Options nosniff;
add_header X-XSS-Protection "1; mode=block";

server
{
        listen         80;
        server_name    sevaho.com;
        return         301 https://$server_name$request_uri;


}


server
{
        error_page  404  /notfound.html;


        listen 443 ssl default_server deferred;


        ssl_certificate /etc/nginx/ssl/cert_chain.crt;
        ssl_certificate_key /etc/nginx/ssl/sevaho.key;


        # enable session resumption to improve https performance
        # http://vincent.bernat.im/en/blog/2011-ssl-session-reuse-rfc5077.html
        ssl_session_cache shared:SSL:50m;
        ssl_session_timeout 5m;
        # Diffie-Hellman parameter for DHE ciphersuites, recommended 2048 bits
        ssl_dhparam /etc/nginx/ssl/dhparam.pem;


        # enables server-side protection from BEAST attacks
        # http://blog.ivanristic.com/2013/09/is-beast-still-a-threat.html
        ssl_prefer_server_ciphers on;
        # disable SSLv3(enabled by default since nginx 0.8.19) since it's less secure then TLS http://en.wikipedia.org/wiki/Secure_Sockets_Layer#SSL_3.0
        ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
        # ciphers chosen for forward secrecy and compatibility
        # http://blog.ivanristic.com/2013/08/configuring-apache-nginx-and-openssl-for-forward-secrecy.html
        ssl_ciphers "ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA:ECDHE-RSA-AES1$


        # enable ocsp stapling (mechanism by which a site can convey certificate revocation information to visitors in a privacy-preserving, scalable manner)
        # http://blog.mozilla.org/security/2013/07/29/ocsp-stapling-in-firefox/
        resolver 8.8.8.8;
        ssl_stapling on;
        ssl_trusted_certificate /etc/nginx/ssl/sevaho_com.crt;


        # config to enable HSTS(HTTP Strict Transport Security) https://developer.mozilla.org/en-US/docs/Security/HTTP_Strict_Transport_Security
        # to avoid ssl stripping https://en.wikipedia.org/wiki/SSL_stripping#SSL_stripping
        add_header Strict-Transport-Security "max-age=31536000; includeSubdomains;";


        root /data/sevaho.com/www;


        gzip on;
        gzip_types text/plain image/jpeg image/png text/css text/javascript;
 error_log /data/sevaho.com/logs/error.log error;
        access_log /data/sevaho.com/logs/acces.log;


        client_max_body_size 10G; # set max upload size
        fastcgi_buffers 64 4K;


        location / {
        index index.html index.htm index.nginx-debian.html index.php;
        }


        server_name sevaho.com;


        location ~ [^/].php(/|$) {
        fastcgi_split_path_info ^(.+?.php)(/.*)$;
        fastcgi_pass unix:/var/run/php5-fpm.sock;
        fastcgi_index index.php;
        include fastcgi_params;
        }
        # ownCloud blacklist
        location ~ ^/owncloud/(?:\.htaccess|data|config|db_structure\.xml|README) {
        deny all;
        error_page 403 = /owncloud/core/templates/403.php;
        }
        location /owncloud/ {
        error_page 403 = /owncloud/core/templates/403.php;
        error_page 404 = /owncloud/core/templates/404.php;


        rewrite ^/owncloud/caldav(.*)$ /remote.php/caldav$1 redirect;
        rewrite ^/owncloud/carddav(.*)$ /remote.php/carddav$1 redirect;
        rewrite ^/owncloud/webdav(.*)$ /remote.php/webdav$1 redirect;


        rewrite ^(/owncloud/core/doc[^\/]+/)$ $1/index.html;


        # The following rules are only needed with webfinger
        rewrite ^/owncloud/.well-known/host-meta /public.php?service=host-meta last;
        rewrite ^/owncloud/.well-known/host-meta.json /public.php?service=host-meta-json last;
        rewrite ^/owncloud/.well-known/carddav /remote.php/carddav/ redirect;
        rewrite ^/owncloud/.well-known/caldav /remote.php/caldav/ redirect;


        try_files $uri $uri/ index.php;
        }


#REVERSE BSD
        location \ /sevaho/bsd/ {
proxy_bind 192.168.0.250;
proxy_pass http://192.168.0.250;
}
#REVERSE-PROXY PYTHON APP 5000
         location ~ /sevaho/projects.* {
         rewrite (/projects)$ / break;
         rewrite /projects/(.*) /$1 break;
  proxy_pass http://127.0.0.1:5000;
         proxy_redirect / /projects/;
         proxy_set_header Host $host;
         proxy_set_header Origin http://$host;
         proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
         proxy_http_version 1.1;
         proxy_set_header Upgrade $http_upgrade;
         proxy_set_header Connection $http_connection;
         }


#REVERSE-PROXY NETDATA 19999
         location ~ /sevaho/netdata.* {
         auth_basic "Protected";
         auth_basic_user_file passwords;
         rewrite (/netdata)$ / break;
         rewrite /netdata/(.*) /$1 break;
         proxy_pass http://127.0.0.1:19999;
         proxy_redirect / /netdata/;
         proxy_set_header Host $host;
         proxy_set_header Origin http://$host;
         proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
         proxy_http_version 1.1;
         proxy_set_header Upgrade $http_upgrade;
         proxy_set_header Connection $http_connection;
         }
}










```

So I need to add this?

```

upstream sevaho.example.com
{
server 192.168.0.250;
}
location @sevaho.example.com{
proxy_pass http://192.168.0.250;
}

```

---

### Post by TheFu on 2016-11-18
I can't answer your question (just add X?). Posted what I know works. Sorry if that isn't helpful.

Appears we are missing each other's points. Too much multi-tasking here today to concentrate. Sorry.

**Feel free to ignore my suggestion:**
My point is not to put a freenas box on the internet. To risky.  HTTPS is broken and shouldn't be trusted.  Documents/files need to be protected by a full vpn or ssh-tunnel using private keys. For example, 
```
$ ssh -f -L 61022:istar:22 gw.example.com -NT

``` creates a tunnel using gw.example.com as a "jump box" to access port 22/tcp on istar.  istar isn't available on the internet, only gw is. This tunnel can be added to the ~/.ssh/config to automatically happen when you want it.  ssh is amazing.  sftp can do similar things - providing access.

As an alternative to putting a webapp on the internet, use ssh-based protocols when you want remote access. There are many clients, which are considered secure. That means you don't need a reverse proxy at all, since the ssh will get you inside your HOME network and access will be available.  Setup an ssh-tunnel and you don't need a reverse proxy and can still use owncloud or sftp or scp or rsync without making all that data available over the internet.  Only the ssh port/tcp needs to be allowed in. Block brute force attacks at the firewall or better, only allow connections from known locations that should have access.

For nginx, every service you want to make available belongs inside a different config file. Nginx expects this. That keeps confusion to a minimal.  For example, my reverse proxy doesn't do anything else - it doesn't run php web-apps. Those happen on other systems, not the same one.  The reverse proxy is in a different "network zone" than the webapp servers or DB servers. There is a firewall between them which only allows the required ports through from the expected machines. This is a basic security architecture idea.  Keep the important data as far away from the internet as possible is another.  Make people use a VPN/ssh-tunnel with key-based authentication, never passwords, to gain access.

Of course, only you know what you really want to accomplish and how to make it happen. Just be aware that the way everyone else does it is sometimes highly non-secure.  Industry standards often suck.

---

### Post by sebastiaan5 on 2016-11-19
It's not that your information was not helpful, my primary question was not that straight-forward, I was trying to forward proxy via Nginx, which is not the best solution, I learned about Forward proxy servers fe. Squid but I think having all this is kinda overkill for what I am just trying to do as an experiment. 

Now to discuss the matter further.

The reason why I don't do the ssh tunneling for FreeNas or Owncloud is purely UI, I mean having a beautiful UI in your browser connecting to your home network is the ultimate utopia right? What I didn't know was that https is so broken, you talking about that https has almost no difference with normal http, do you mean that to all https or ssl certs in specific? I know there are ssl cert companies which are corrupt/broken/whatever but don't you think companies like Comodo for example is a good one?

I connect already to my windows server via an ssh tunnel, very secured, everything on it, but having your complete OS fe. FreeNas connecting from anywhere is kinda cool.

I connect with this script to my windows server, I use knockd to have a bit more security (if there is anything you would change please tell me I like to know, private information is hidden of course):

```

#!/bin/bash

knock 78.21.146.15 <port>:tcp <port>:tcp <port>:tcp
sleep 1

echo 'Set X and Y by passing $1 $2.'

if [[ $1 -eq 0 || $2 -eq 0 ]]; then

ssh -fL 3389:192.168.0.3:3389 <USER>@78.21.146.15 sleep 5
rdesktop -x I -z -K -k nl-be -u xxx -p xxx -g 1600x1000 localhost:3389
else

ssh -fL 3389:192.168.0.3:3389 <USER>@78.21.146.15 sleep 5
rdesktop -x I -z -K -k nl-be -u xxx -p xxx -g $1x$2 localhost:3389
fi

knock 78.21.146.15 <port>:tcp <port>:tcp <port>:tcp



```

So my question for the FreeNas thing now is is there like a solution where UI meets security? I can do the same of course like my windows server and just use remote desktop trough an ssh tunnel. But maybe you are thinking of other options?

ps. what does the -T option do in your ssh example, the manual says "Disable pseudo-terminal allocation." This means you don't open a terminal on your "jump box"?

---

### Post by TheFu on 2016-11-21
I've never used nginx as a "forward proxy" only as a "reverse proxy."  Squid is the normal proxy or clients going outbound.

Using that ssh tunnel, you can have exactly the pretty web GUI.
Or you can use ssh as a SOCKS proxy into your network. **ssh -f -D 64000 gw.example.com -NT**. Then just set the SOCKS proxy in the browser or OS to use localhost:64000.  

If you want to use a reverse proxy with SSL, the nginx should be the SSL termination point and point to a backend that doesn't have SSL.

HTTPS is a house of cards. [https://www.eff.org/deeplinks/2011/10/how-secure-https-today](https://www.eff.org/deeplinks/2011/10/how-secure-https-today)

Just to clarify, it isn't SSL that is the issue (sure, there have been bugs, but ...). It is the dependence on external DNS and external Certs that are the issue.  Do govts really care about our HTTPS traffic?  Cannot say, but if there is an automatic way to read it, I think they will. AND I think they do. Cannot say why, but ...   er .... they do.

I don't use port knocking - just lazy on my part.  I do use fail2ban and never use passwords for authentication, always keys.

When I need a remote desktop, I hop onto a Linux system running x2go (which uses NX and is 2-3x faster than VNC or RDP) and NX uses ssh for tunneling.  Then, from that desktop, use normal RDP to a Windows machine running on the same host.  People that switch to NX say it is like night & day compared to VNC or RDP. NX servers only run on Linux. There are clients for the 3 main desktop platforms. I know the windows and linux clients work well.  So ... Linux via ssh/x2go --> [fw] --> Linux --> RDP  Basically, anything I can do on my LAN, I can do remotely, with just 1 port (ssh) open.

Having just that single port open means we can use 
* a remote terminal
* transfer files with either scp or sftp or rsync
* backup files with any backup tool based on librsync (rdiff-backup and probably 10 others); also restore files
* remotely edit files with vim via rsync - it's a vim thing.
* have a fast, secure, remote desktop from anywhere in the world
* or use ssh for all the magic tunneling/proxying, forward and reverse tunnels we like.  ssh is amazing.
all with just 1 port open for private access to the network or specific services running on the remote LAN or anywhere on the internet.

I missed what the client was that you wanted to use?  I use a bunch when remote, going through different ssh connections (sorta like a VPN) to access my home network or have all web traffic go through my home network before hitting the internet.

BTW, I think your use of ssh tunnel for RDP is sufficiently secure. My method above isn't any more secure than yours, unless the ssh is terminated on a router that isn't able to be patched weekly. **Then you have a security issue.**  I don't consider any consumer routers viable for use facing the internet.  Until today, the Apple router could have been viable, but now that apple has ended support, forgetaboutit.  If the routers aren't patched weekly,  I don't consider it secure.  Didn't always feel this way, but in the last 5 yrs I've slowly determined that router firmwares just aren't maintained properly. Only if we use normal distros (Linux/BSD) and configure our own router can we be _mostly_ secure.  Plus, I'm willing to spend much more cash on quality HW for the router if I know it will last 10+ yrs AND be maintainable.  Got a $144 device, runs Linux, uses 10W max, supports AMD-v and has 4 Intel PRO/1000 NICs. The perfect router, perhaps?

Of course, since I also run public services on other IPs at the house, those are each open to many subnets. Private services are locked down to only those subnets which actually need access, not the entire internet. Most of the internet is blocked for company/private access.

I've never run FreeNAS, but if it supports ssh, then it supports sftp, so you can use sftp for remote file access, correct?  If you run something like Nextcloud, I can assure you that the SOCKS proxy works perfectly for web access to it.  Also works with wallabag and plex media server. ;)  Watched a hidef video yesterday afternoon when away from home, streamed to the location I was at (only 10 miles away, but could have been across the world).  Streaming audio via plex "just works", since there really isn't any bandwidth limits these days if connectivity exists.

Yes, the -T just prevents a tty from being allocated. There are subtle reasons to have a tty and other reasons not to have a tty. For a tunnel, why suck up a resource if it isn't necessary?

Did you get nginx working after simplifying each config to a single file?

---

### Post by sebastiaan5 on 2016-11-22
Thank you for such an informative reply.

First of all I cleaned up my nginx config, it works as it used to be. There was nothing wrong with it I think I don't have many configurations just Netdata and Owncloud (and experimental stuff).

You are saying that I can use SOCKS proxy to get to my server via web, this is a bit frustrating I guess because you need to configure your browser every time to use the right SOCKS.
 
I use rdeskop as client, it's quite lovely because it's pure terminal based, I have it in a script and directly after launching my server reveals itself.
Now I'm trying to install x2go but I have some issues. My set up is as follows: 

Fedora 24 -> RaspberryPI3 -> Windows Server2012

So my question is do I need port 22 to be also open on windows server or can I use 5900 and which NX server should I install on windows? NoMachine any good?

Greetings

---

### Post by TheFu on 2016-11-22
Don't think you can use x2go with that setup. Has it been ported to ARM?  You need more Linux, less Windows.  Windows is a client, not a server, in the x2go world. Also, a remote desktop is not "terminal based", so that statement is confusing.

Not all NX systems are compatible.  x2go-client only works with x2go-server. Over the years, I've used 3 different NX setups. Never used the NoMachine server - it isn't F/LOSS. Free but closed source is an issue for me.

As for using SOCKS and a browser, why not script it?  2 lines. Not hard.  And it only need be used when you are remote.

But we are WAY OT not. Bye.

---

### Post by sebastiaan5 on 2016-11-22
You are right, it's getting out a hand, so many new questions I will search the internet :)

ps. I would use everything in Linux, I just need Windows for school to program in visualstudio ;) Remote is kinda the best solution, dual booting is to slow :p

---


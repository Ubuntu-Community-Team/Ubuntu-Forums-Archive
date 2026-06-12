---
title: "Apache 2.2 reverse proxy for subsonic not working!"
date: 2011-05-26
forum: Server Platforms
---

### Post by fifa255 on 2011-05-26
Hi all,

I have apache 2.2 installed on mu Ubuntu 11.04 natty platform.  I also have subsonic music streaming service installed which listens to port 4040 for http and 4443 for https.  I am trying to set up reverse proxy so that [http://ip-address/music](http://ip-address/music) will redirect me through the reverse proxy to [http://ip-address:4040/music](http://ip-address:4040/music).  
I have the following modules loaded proxy, proxy_http and I am using the below config file to set up the reverse proxy after reading through apache documentation and forums.

ProxyRequests Off
ProxyPreserveHost Off
<Proxy *>
    Order deny,allow
    Allow from all
</Proxy>
ProxyPass /music [https://localhost:4443/music](https://localhost:4443/music)
ProxyPassReverse /music [https://localhost:4443/music](https://localhost:4443/music)


So far this will work only on the machine the apache server and subsonic is installed on (ip address on lan 10.0.0.8).  However if I try to access the subsonic server from a different ip/machine on my lan it will redirect to localhost:4443 which will not work as subsonic server is not running on this machine.  Does anyone have an idea why this would not be working.  I have searched on google and for the most part everyone seems to be using a very similar config file for reverseproxy.  Any help is appreciated.  Thanks.

I have attached a screeshot of the firefox error that I get when trying to access the apache server machine from a different computer on the lan.

---

### Post by boutch55555 on 2011-05-28
Tried replacing ```
ProxyPass /music https://localhost:4443/music
ProxyPassReverse /music https://localhost:4443/music
```
with
```
ProxyPass /music https://10.0.0.x:4443/music
ProxyPassReverse /music https://10.0.0.x:4443/music
```
?

---

### Post by fifa255 on 2011-05-31
boutch55555,

Thanks for your reply.  I tried your suggestion earlier. But doing so will only make this work on my LAN (10.0.0.* subnet).  If I try to access my server from the internet (from a different network) [http://external-ip/music](http://external-ip/music) then it will redirect the browser to [https://10.0.0.8:4443/music](https://10.0.0.8:4443/music) which does not exist.  Any other suggestions.

---

### Post by boutch55555 on 2011-06-01
You could setup a dyndns / noip service and replace it in the config :
```
ProxyPass /music https://myhome.dyndns.org:4443/music
ProxyPassReverse /music https://myhome.dyndns.org:4443/music
```

You then need to redirect the ports on your router to the correct hosts. It probably won't work from your local network though.

I don't have much experience with apache as a proxy, I usually use nginx for this task, but there must be a way to get apache to do the url rewriting right...

Tried to put ProxyPreserveHost to On ?

---


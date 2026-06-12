---
title: "apache proxy redirect issues"
date: 2013-01-29
forum: Server Platforms
---

### Post by m12lrpv on 2013-01-29
I'm struggling with some config and I need some help.

_My Environment:_
My environment consists of an xbmcbuntu machine running headless as a NAS with linux raid and transmission on it. I'm very happy with that.

On the network I have a thecus NAS device which has a web interface which is stored on a ROM (i.e. not editable).

I use dyndns to map my allocated dynamic IP address on the WAN.

Due to limitations at work I am restricted to using the SSL port 443 for my connections.

I have installed apache on my xbmcbuntu machine and I want to use it to redirect from my.dyndns-server.net:443 to all of the other web interfaces. I also want it to work with the internal ip's but internally it will use both port 80 and ssl port 443.

Server version: Apache/2.2.20 (Ubuntu)
Server built:   Nov  6 2012 20:29:14

Linux version 3.0.0-30-generic-pae (buildd@lamiak) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #47-Ubuntu SMP Wed Jan 2 22:57:16 UTC 2013


_Desired Configuration:_

My server internal IP: 192.168.1.2
My Dyndns : my.dyndns-server.net

Mappings for WAN access:

[https://my.dyndns-server.net/thecus](https://my.dyndns-server.net/thecus)         redirected  to either http or [https://192.168.1.5/](https://192.168.1.5/)
[https://my.dyndns-server.net/transmission](https://my.dyndns-server.net/transmission)   redirected  to                [http://192.168.1.2:9091/](http://192.168.1.2:9091/)
[https://my.dyndns-server.net/](https://my.dyndns-server.net/)               not redirected                [https://192.168.1.2/](https://192.168.1.2/)

Mappings for LAN access:
[https://192.168.1.2/thecus](https://192.168.1.2/thecus)         redirected  to          [https://192.168.1.5/](https://192.168.1.5/)
[http://192.168.1.2/thecus](http://192.168.1.2/thecus)          redirected  to          [http://192.168.1.5/](http://192.168.1.5/)

[https://192.168.1.2/transmission](https://192.168.1.2/transmission)   redirected  to          [https://192.168.1.2:9091/](https://192.168.1.2:9091/)
[http://192.168.1.2/transmission](http://192.168.1.2/transmission)    redirected  to          [http://192.168.1.2:9091/](http://192.168.1.2:9091/)

[https://192.168.1.2/](https://192.168.1.2/)               not redirected          [https://192.168.1.2/](https://192.168.1.2/)
[http://192.168.1.2/](http://192.168.1.2/)                not redirected          [http://192.168.1.2/](http://192.168.1.2/)

The transmission redirect using mod_proxy was simple and well within my apache capabilities but the redirect to the Thecus NAS box is proving to be beyond the ability of google to solve and I've reached the point where I need to seek the help of others.

The transmission configuration:
```

RewriteEngine on

# Redirect requests to /transmission to /transmission/web
RewriteRule /transmission[/]?$ /transmission/web [R=permanent]

ProxyRequests Off
<Proxy *>
  Order Allow,Deny
  Allow from all
</Proxy>

ProxyPass /transmission/ http://localhost:9091/transmission/
ProxyPass /transmission http://localhost:9091/transmission

ProxyPassReverse /transmission http://localhost:9091/transmission
ProxyPassReverse /transmission/ http://localhost:9091/transmission/

```The core issue is that the web interface on the Thecus NAS box seems to be using direct links to it's html instead of relative links. Proxypass doesn't redirect them well. I get errors saying that [http://192.168.1.2/thecushtml.htm](http://192.168.1.2/thecushtml.htm) doesn't exist.

I tried the config from here [http://www.apachetutor.org/admin/reverseproxies](http://www.apachetutor.org/admin/reverseproxies) where the author seems to understand the issue however it still refused to work. I was getting the same errors.

I suspect that part of the issue was version differences in apache and it's modules. Everything that google turns up is related to wholly different versions.

Now I understand that there is probably a long list of things i'm doing wrong which are not worth discussing which leads me to my question... 

_Question:_

How do I correctly configure apache to make my desired configuration work?

---

### Post by cariboo on 2013-01-30
If the network owner has measures in place to secure their network, it's up to you to ask for an exception, as we don't support this type of activity here. Thread closed.

---


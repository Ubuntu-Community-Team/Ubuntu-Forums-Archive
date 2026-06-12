---
title: "Apache2 ReverseProxy for Port 8080-&gt;80"
date: 2010-07-27
forum: Server Platforms
---

### Post by sunchobe on 2010-07-27
Hi,

I have an Ubuntu running and I developed a webapplication using jetty. Now that I want to deploy and run my application on my server, the application starts on port 8080. 

Usually this port is not available if you are in a very restrictive environment and therefore  I cannot access the webapp when I am e.g. in my company. To solve this problem I would like to configure my apache that way, to redirect all requests accessing 

*[http://sunchobe.homelinux.com/volleyvz/](http://sunchobe.homelinux.com/volleyvz/) *

internally to the running webapp 

*[http://localhost:8080/volleyvz/](http://localhost:8080/volleyvz/)*

I was trying to use ipchains, iptables etc. but nothing worked and at least I found the solution I would like to prefer, if I can make it work: ReverseProxy.

I configured my according virtual host using the following:

[I]<VirtualHost sunchobe.homelinux.com:80>

   ServerName sunchobe.homelinux.com
   DocumentRoot /var/www/volleyvz

   ProxyRequests Off
   ProxyPass /volleyvz [http://localhost:8080/volleyvz/](http://localhost:8080/volleyvz/)
   ProxyPassReverse /volleyvz [http://localhost:8080/volleyvz/](http://localhost:8080/volleyvz/)
   <Location /volleyvz/>
     RequestHeader unset Cookie
     RequestHeader unset Referer
   </Location>
</VirtualHost>[/I]

I loaded the needed modules and restarted the apache (more than once ;))

Maybe I did something wrong in my configuration or somewhere else, but I do not know where to look for logs or something to find our what my problem is. The apache-logs seem not to be very communicative at this point. 

Any suggestions? How can I solve my problem?

Bye,
Christian.

---

### Post by chopinhauer on 2010-07-27
I don't see any real problem with your configuration, but there is a small typo that can give unexpected results:

> **sunchobe said:**
> [I]
   ProxyRequests Off
   ProxyPass /volleyvz [http://localhost:8080/volleyvz/](http://localhost:8080/volleyvz/)
   ProxyPassReverse /volleyvz [http://localhost:8080/volleyvz/](http://localhost:8080/volleyvz/)
   [/I]

If the first argument to **ProxyPass** has a trailing '/', the second should also have one and viceversa. Same for ProxyPassReverse.

You might also adjust the permissions on the proxy with:
```

<Proxy *>
Order Deny,Allow
Allow from all
</Proxy>

```
It is safe since you deactivated the forward proxy.

To rewrite URI also inside the generated HTML, you might be interested by mod_proxy_html. There is a [tutorial]("http://www.apachetutor.org/admin/reverseproxies") that explains how to use it (and how to configure reverse proxies in general).

---


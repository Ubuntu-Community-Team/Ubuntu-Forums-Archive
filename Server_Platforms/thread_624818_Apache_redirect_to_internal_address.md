---
title: "Apache redirect to internal address"
date: 2007-11-27
forum: Server Platforms
---

### Post by self-defence on 2007-11-27
Hi,

I've got a server binded to a domain that is accessible form the external network. This is the part that works.
But I've no idea on how to do the following. I've got another server on the same internal network as the online server and there is an application running on it that I would like to make it reachable on the external network via the main server.
Something like this [http://sub.domain.com/theapplication/](http://sub.domain.com/theapplication/) on the main server that would actually be [http://192.168.1.3/aplication/](http://192.168.1.3/aplication/).

Can this be done?

Thanks for the help and nice day.

---

### Post by MJN on 2007-11-27
It can indeed be done!
 
Assuming the internal application server is not accessible directly from the outside then what you need is the Apache mod_proxy module and, in particular, the ProxyPass directive - see [http://httpd.apache.org/docs/2.0/mod/mod_proxy.html#proxypass](http://httpd.apache.org/docs/2.0/mod/mod_proxy.html#proxypass) (note the warning about turning ProxyRequests off).
 
I will leave the rest up to you as a learning exercise however if you get seriously stuck do shout (and of course if anyone wants the gold stars then please do feel free to post the readymade config - don't let me decide the rules!).
 
Mathew

---

### Post by self-defence on 2007-11-27
MJN -> Thank you I was able to enable the modules needed. I also added the directive and something seems to be working. Because the "not found" message I now get "forbidden" no matter where I point the   directive to.

The modules I just linked form /etc/apache2/mods-available/proxy*.* to /etc/mods-enabled/proxy*.*. And the modules are enabled since phpinfo shows the modules.

I added ProxyPass /app [http://192.168.1.10/application](http://192.168.1.10/application) but as I said I only get the "forbidden" message. 

I'm not really sure what to do now.

Thanks for the help and good night.

---

### Post by MJN on 2007-11-28
> **self-defence said:**
> The modules I just linked form /etc/apache2/mods-available/proxy*.* to /etc/mods-enabled/proxy*.*. And the modules are enabled since phpinfo shows the modules.
 
You ought to to use the a2enmod and a2dismod helper scripts to do the linking, however it sounds like you've done the right manual steps anyway to get it enabled.
 
> I added ProxyPass /app [http://192.168.1.10/application](http://192.168.1.10/application) but as I said I only get the "forbidden" message. 
 
Check your logs (access and error)...
 
Mathew

---

### Post by self-defence on 2007-11-28
I checked the logs.
The only thing that is in the error log is this:
```

[notice] SIGHUP received.  Attempting to restart
[warn] module proxy_http_module is already loaded, skipping
[notice] Apache configured -- resuming normal operations
[error] [client ***.***.***.***] client denied by server configuration: proxy:http://192.168.1.8/app/

```
It seems that the proxy module is already loaded but I don't think that this is the root of my problem.

And the access log actually doesn't exists. I haven't figured the cause of that. But I'll fix that.

So the error message is still there. It's like I don't have permission to access the internal network or something. Even tho the servers are on the same network and can access one another just fine.

I'm currently out of ideas.

Nice day to all

---

### Post by MJN on 2007-11-28
> **self-defence said:**
> I checked the logs.
The only thing that is in the error log is this:
```

[notice] SIGHUP received.  Attempting to restart
[warn] module proxy_http_module is already loaded, skipping
[notice] Apache configured -- resuming normal operations
[error] [client ***.***.***.***] client denied by server configuration: proxy:http://192.168.1.8/app/

```
 
That's exactly it - it's telling you access to the location is disallowed (actually because it hasn't been explicitly allowed). It's not you that doesn't have permission, but rather the client (okay, that is you but you know what I mean!).
 
Try adding the following:
 
```
<Proxy http://192.168.1.8/>
Order Allow,Deny
Allow from all
</Proxy>
 
..although I've also seen the following used:
 
<Directory proxy:http://192.168.1.8/>
Order Allow,Deny
Allow from all
</Directory>
```
 
Mathew

---

### Post by self-defence on 2007-11-30
Hey
MJN -> thanks it seems to work but only if I'm on the same network as the two servers. When I try accessing the URL from the internet it just changes the address to the local one.

Any ideas?

Bye

---

### Post by MJN on 2007-11-30
Are you sure its not the application server that's redirecting (to itself i.e. a local machine)?

You could try adding the following:

[B]ProxyPassReverse /app [http://192.168.1.10/application](http://192.168.1.10/application)

[/B]to rewrite the headers in the reverse direction.

Depending on what you backend application is you may also need to use the ProxyPreserverHost directive (see the docs) although I suspect the backend server is unaware of your frontend server's name.

Mathew

---

### Post by self-defence on 2007-12-10
Thank you MJN it works. :)
Just the reverse was missing and it started to work the moment I added it.

Best regards.

---


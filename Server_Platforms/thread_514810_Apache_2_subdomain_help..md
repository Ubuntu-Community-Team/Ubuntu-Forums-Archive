---
title: "Apache 2 subdomain help."
date: 2007-08-01
forum: Server Platforms
---

### Post by LinuxLappy on 2007-08-01
I'm running into a roadblock. I'm trying to setup a sub domain on my apache2 server. The server is on Linux if that helps. I want the subdomain to point at a different computer on my network. It's running IIS 6.0. Any idea how to config the apache 2 server to point at the IIS server when I goto sub.domain.com.

The apache server has a public port of 80 and a private IP of 192.168.1.1
The IIS server has a public port of 81 and a private IP of 192.168.1.5.

Can you also give me a sample config of the v host. Thanks!

---

### Post by kidders on 2007-08-02
Hi there,

Your post is confusing. What does your Apache configuration have to do with an IIS server running on a different machine? Is there some reason why you want to somehow involve your Apache server in requests sent to your IIS box?

---

### Post by coastdweller on 2007-08-02
> **kidders said:**
> Hi there,

Your post is confusing. What does your Apache configuration have to do with an IIS server running on a different machine? Is there some reason why you want to somehow involve your Apache server in requests sent to your IIS box?

I think I understand the OP.

They have Apache serving their domain, they want the IIS server to serve up a subdomain.

Example: 

domain.com > Apache
sudomain.domain.com > IIS

I suppose the answer lies in virtual hosts where the apache redirects to the local IP of the IIS box after reaching the Apache box.

---

### Post by MJN on 2007-08-02
That's not necessary given the current server configuration - the servers are running on different ports and so the router will be quite able to forward each individually.

The OP really needs to elaborate on exactly what they want to achieve - I would've thought they'd wish to avoid having to run the sub-domain off a non-standard port (to save having to use it the URL) in which case proxying in Apache would probably the best solution.

If they do wish to use the standard port for both domains then try the following for size, although note I have no personal experience of this and so am basing it on theory alone:

```

<Virtualhost *:80>
   Servername domain.com
   ...all your Linux server config for domain.com
</Virtualhost>

<Virtualhost *:80>
   Servername sub.domain.com
   Proxypreservehost On
   Proxypass / http://192.168.1.5:81/
   Proxypassreverse / http://192.168.1.5:81/
</Virtualhost>
```Check out further info at [http://httpd.apache.org/docs/2.0/mod/mod_proxy.html](http://httpd.apache.org/docs/2.0/mod/mod_proxy.html)

With this all requests to port 80, regardless of domain, will be sent to the Apache server by the router. Apache will handle requests for domain.com itself whereas for sub.domain.com requests it will pass these on to the IIS server. The response from the IIS server will then be passed back to the client.

Note also that you would not need to run the IIS server on port 81 anymore (get rid of the :81 in the above code if you change this). Again, it all depends on what you're trying to achieve as to which way you'd want to take it.

Mathew

---


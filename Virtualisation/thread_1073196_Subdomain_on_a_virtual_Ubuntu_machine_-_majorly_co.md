---
title: "Subdomain on a virtual Ubuntu machine - majorly confused"
date: 2009-02-18
forum: Virtualisation
---

### Post by wubbzy on 2009-02-18
I'm doing web programming for someone who set up Ubuntu as a virtual machine on his machine (acme.com). The virtual machine has its own domain name (xyz.com). In other words, I SSH into xyz.com to do my web programming, and that site is served up as xyz.com. The /etc/hosts looks like this:

127.0.0.1       localhost
127.0.1.1       xyz.acme.com        xyz

I want to set up a subdomain as a test site, something that would b at [http://test.xyz.com](http://test.xyz.com). How do I do that? I followed instructions for regular instances of Linux and modified the /etc/hosts file like this:

127.0.0.1       localhost
127.0.0.2       test.xyz.com
127.0.1.1       xyz.acme.com        xyz

But that doesn't work. What am I supposed to do? I did create a second website under /etc/apache2/sites-available, ran a2ensite, and restarted apache. I think I'm not setting up the /etc/hosts file correctly.

Help! Thanks!

---

### Post by the_unforgiven on 2009-02-18
You need to create a VirtualHost in apache for that to work. Web content servicing is not *only* about resolving hostname to IP address - it's *also* about how the web-server is configured.

Use [Apache's NameVirtualHost]("http://httpd.apache.org/docs/2.2/vhosts/") directive.

HTH ;)

---

### Post by wubbzy on 2009-02-18
> **the_unforgiven said:**
> Use [Apache's NameVirtualHost]("http://httpd.apache.org/docs/2.2/vhosts/") directive.

Thank you. That was something I didn't know about. It doesn't solve my problem, however.

The apache directives for my subdomain is in
   /etc/apache2/sites-available/test
and in it, I put in the NameVirtualHost directive, like this:
```
NameVirtualHost 127.0.0.2
<VirtualHost 127.0.0.2>
    ServerName test.xyz.com
    ServerAlias test.xyz.com
    ... plus other stuff ...
</VirtualHost>
```

And in my /etc/hosts I have:
```
127.0.0.1   localhost
127.0.0.2    test.xyz.com
127.0.1.1    xyz.acme.com   xyz
```
The second line is what I inserted in my attempt to create a subdomain.

I think the problem is that my virtual machine is *already* a subdomain on acme.com, but it's set up appear as its own domain. So regular methods for creating a subdomain doesn't quite work. I have no idea how virtual machines work, so I don't know how to sort this out.

Any ideas on how to make this work, anyone???

---


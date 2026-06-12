---
title: "web server monitoring/routing/failover - possible?"
date: 2008-09-16
forum: Server Platforms
---

### Post by fluffyllama on 2008-09-16
Hi all, I'm wondering if it's possible to use Ubuntu to monitor an existing Win2k3/4D web server and provide a failover capability.

Basically, we have a web server running 4D on Win2k3, and for those who don't know, 4D is unstable at the best of times...  Our corporate web site has been around for about 12 years, running on various versions of 4D, and our SEO guys tell us that we can't use redirects or subdomains since that'll kill our Google rankings.  We are unable to migrate our web page to something nicer like Apache, since the pages are coded to something specific in 4D.  

What we want to do is set up an intermediary box of some sort to route web traffic through it.  Basically, the (hopefully) Ubuntu server will take all the web requests and route them to a different machine based on URL, lets say [www.tester.ca/1234](www.tester.ca/1234) goes to one IP, and [www.tester.ca/5432](www.tester.ca/5432) goes to another IP.

Is this possible?  Sorry for the bad explanation, I'm not entirely sure how this is supposed to work :p

---

### Post by alastair on 2008-09-16
> **fluffyllama said:**
> Is this possible?  Sorry for the bad explanation, I'm not entirely sure how this is supposed to work :p

Yes, I think this is "bread and butter" sort of stuff. Never set it up or used it myself, but it is the sort of thing that Apache mod_proxy might do e.g.

[http://httpd.apache.org/docs/2.2/mod/mod_proxy.html](http://httpd.apache.org/docs/2.2/mod/mod_proxy.html)

> A reverse proxy (or gateway), by contrast, appears to the client just like an ordinary web server. No special configuration on the client is necessary. The client makes ordinary requests for content in the name-space of the reverse proxy. The reverse proxy then decides where to send those requests, and returns the content as if it was itself the origin.

There will be other mechanisms available as well. Maybe the above is a good starting point.

Alastair

---

### Post by fluffyllama on 2008-09-16
This looks like a great start.  Thanks!

Do you happen to know if this supports wildcards? I forgot to specify originally...  Our site is kinda crazy this way  o_O

---

### Post by fluffyllama on 2008-09-18
Ok, I have a working reverse proxy now, despite the apparent lack of documentation on how to set it up (as in a n00b-friendly version)...  I still need to figure out how to use wildcards though.  Basically what I need is [www.test.com/######](www.test.com/######) to point to one machine, and [www.test.com/info.html](www.test.com/info.html) to point to the other (or to apache on this machine, either way).

Can this be done with Apache?  I can't seem to find a lot in the documentation, but I'll have another read through it.

*edit*

Probably better would be to say that certain files/folders are pointed to one machine, and everything else goes to the other machine, if that's any easier...  Also, I need to figure out how to pass through ssl...

---

### Post by RealPSL on 2008-09-19
You may also want to take a look at this which is a slight deviation. What it would allow is for you to have multiple application servers running the same content and the mod_proxy_balancer would route the requests to each one using an algorithm.

[http://httpd.apache.org/docs/2.2/mod/mod_proxy_balancer.html]("http://httpd.apache.org/docs/2.2/mod/mod_proxy_balancer.html")

As for passing SSL mod_proxy supports SSL. What would happen here is the actual certificate would need to be on the proxy or load balancer host. Now this would leave the traffic between the prixy and the actual application server unencrypted. What you can do there is use self-signed certificates on the application servers and then trust those certificates on the proxy. You can then use the [SSLProxyEngine]("http://httpd.apache.org/docs/2.0/mod/mod_ssl.html#sslproxyengine") directive to communicate securely from proxy to application server if this is required.

---

### Post by fluffyllama on 2008-09-19
I did take a look at mod_proxy_balancer, but this probably wouldn't work for us as we are unable to run more than 1 license of the 4D server software.  It would also take a lot of recoding since we have a database on the same server.  Our main idea was to have our landing page on something stable (Apache), but forward any requests for the dynamic content to the original server.

I'll take another look at the ssl, but does anyone know what the correct format for the .pem files should be?  I grabbed the certs from the original server which have these file names:
cert.pem
key.pem
public_key.txt
request.txt

Opening them gives me, in order, 2 certificates, an RSA private key, an RSA public key, and a certificate request.  Apache complains about every file I try to use, though works fine with a .pem I generated...

Also, I still need to figure out how to define ProxyPass with wildcards, so that any folder starting with a 01- will redirect to the old server, or if any file that's not found on one server will be searched for on the other server.  Is this possible with Apache, or should I look at Squid, Pound, or something else, or is this even possible at all?  

So far I have the landing page on my test box, with a few of the main pages redirected to the old box, but our site has thousands of product numbers accessible by [www.tester.com/##-####](www.tester.com/##-####), which I'd rather not update daily, and which can't be changed thanks to the massive amount of printed material out there with these url's....

Any help is appreciated, and all help so far deserves many thanks!

*edit Sept 19*

Also, can I change the thread title?  It's not entirely relevant to my current questions anymore...

*edit Sept 22*

I figured out how to forward product numbers through the proxy, and I ended up using mod_rewrite to do this.  Basically, I have anything starting with /02-#### trigger the rewrite engine, and it rewrites the url and passes this to the proxy engine.

---

### Post by alastair on 2008-09-25
And recently mentioned on Slashdot :

Varnish
[http://varnish.projects.linpro.no/](http://varnish.projects.linpro.no/)

Varnish is a state-of-the-art, high-performance HTTP accelerator. It uses the advanced features in Linux 2.6, FreeBSD 6/7 and Solaris 10 to achieve its high performance.

Some of the features include

* A modern design
* VCL - a very flexible configuration language
* Load balancing with health checking of backends
* Partial support for ESI (the sensible part of ESI)
* URL rewriting
* Graceful handling of "dead" backends


and :

POUND - REVERSE-PROXY AND LOAD-BALANCER

[http://www.apsis.ch/pound/](http://www.apsis.ch/pound/)

The Pound program is a reverse proxy, load balancer and HTTPS front-end for Web server(s). Pound was developed to enable distributing the load among several Web-servers and to allow for a convenient SSL wrapper for those Web servers that do not offer it natively. Pound is distributed under the GPL - no warranty, it's free to use, copy and give away.

---


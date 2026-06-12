---
title: "Apache Error 502 With IIS"
date: 2008-02-05
forum: Server Platforms
---

### Post by Keymaster on 2008-02-05
Ok.  I have Apache on Ubuntu set up as my web server.  I also have it as a proxy for the subdomain crimson.emparc.net (yes I am using actual domain names so you can see the error if you try to visit it)  crimson.emparc.net is supposed to forward to my Win 2k3 with IIS 6.0 so I can access Exchange OWA on port 80.  Sometimes it works, but sometimes it gets the error ```
Proxy Error

The proxy server received an invalid response from an upstream server.
The proxy server could not handle the request GET /Exchange/.

Reason: Error reading from remote server
```
After much Google searching I **THINK** this is an issue with IIS but I'd appreciate help with either if anyone knows the issue, and a fix.  This server setup is for my small business, so I need this to work ASAP.  Thanks guys.

---

### Post by twistedtwig on 2008-02-05
I have a similar problem, but as of yet no solution either.

I have my main server (Ubuntu Apache box) as the main website and use proxypassreverse to get to my 2003 server which is inside my network.  it does work and I can use URL's inside my network to access the windows machine. 

But I do get that error, if I refresh the page it works just fine (normally) but it is not good business to see a page like that from the users point of view.  Don't know how many people I would have lost because of it.

---

### Post by Keymaster on 2008-02-05
I tried disabling http keep alives as Google searching showed that as a fix, but then I can't login in to Outlook Web Access

---

### Post by twistedtwig on 2008-03-01
I seem to have found an answer to this, (well at least I can not get my site to throw a 502 error now).

After a number of Google sessions I came across this site:

[http://www.usenet-forums.com/apache-web-server/41774-reverse-proxy-errors.html](http://www.usenet-forums.com/apache-web-server/41774-reverse-proxy-errors.html)

Which at the bottom says:

```
SetEnv force-proxy-request-1.0 1
SetEnv proxy-nokeepalive 1
```

giving:

[http://httpd.apache.org/docs/2.0/mod/mod_proxy.html](http://httpd.apache.org/docs/2.0/mod/mod_proxy.html)

as a reference

I put the above above code into my virtual host where the proxypass is going on and all seems well.

fingers crossed it can help you (if you have not already found an answer).

---


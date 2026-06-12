---
title: "Can I make apache rewrite links? (mod_proxy_html?)"
date: 2008-05-23
forum: Server Platforms
---

### Post by kebes on 2008-05-23
My general problem here is that I want links in HTML that I'm serving to be re-written. (I don't want to redirect incoming URL requests, like what mod_rewrite does.) Basically in pages that Apache sends out, I want various links to be altered, so that instead of (for example):
```
<a href="http://example.com/image1.jpg">
```
it gets switched to:
```
<a href="http://otherdomain.com/image1.jpg">
```


Obviously what I need is some kind of regex-capable text filter that Apache applies to any HTML request.

I found and installed the Apache module called "[mod_proxy_html]("http://apache.webthing.com/mod_proxy_html/")". It has a function called [ProxyHTMLURLMap]("http://apache.webthing.com/mod_proxy_html/config.html") which seems to do exactly what I want: it allows for regex-style search-and-replace. And it is restricted to only rewriting URLs.

This is perfect... except that it appears it was written specifically to work in reverse proxy situations. So when I try to use it by itself, e.g. by adding: 
```

SetOutputFilter proxy-html
ProxyHTMLURLMap http://example.com http://otherdomain.com

```
to "/etc/apache2/sites-available/default", I don't get any changes at all. I turned on proxy-html's verbose logging, by adding:
```

ProxyHTMLLogVerbose On
LogLevel Info

```

And then in /var/log/apache2/error.log I see messages like:
```
Non-proxy request; not inserting proxy-html filter
```


So it seems that I cannot use ProxyHTMLURLMap on it's own. I have to use it as part of a proxy or reverse proxy setup? All the guides I find online (e.g. [this one]("http://www.apachetutor.org/admin/reverseproxies")) describe how to use it in a proxy setup.

So my questions are:
1. Does anyone know of a means of rewriting links in web-pages that Apache serves (that doesn't have a huge performance penalty like [mod_ext_filter]("http://httpd.apache.org/docs/2.0/mod/mod_ext_filter.html"))?
2. Can anyone see a way to invoke ProxyHTMLURLMap in a non-proxy situation? Is there a way to 'trick' it into running (enabling the proxy module without actually doing any redirects)?


I guess this is a somewhat esoteric problem. Any help or ideas are certainly appreciated.

---

### Post by RealPSL on 2008-07-13
As far as tricking it to work like a proxy why not put a Virtual Host in place that does the proxying of your web site. That would mean double work for your apache server but it would certainly allow you to solve the problem.  Obviously that comes with a performance penalty but I am not sure how much. I am not going to go into Virtual Host setups because you seem very competent with Apache.

---

### Post by kebes on 2008-07-15
> **RealPSL said:**
> why not put a Virtual Host in place that does the proxying of your web site. That would mean double work for your apache server but it would certainly allow you to solve the problem.

Thanks for the suggestion. In the end, I just used mod_rewrite to redirect the requests to the other web-object. It wasn't exactly what I wanted, but it did the job (and a request that gets redirected is, I'm assuming, pretty light-weight).

Thanks again.

---


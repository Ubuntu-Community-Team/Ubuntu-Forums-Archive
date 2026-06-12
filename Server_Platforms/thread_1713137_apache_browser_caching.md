---
title: "apache browser caching"
date: 2011-03-23
forum: Server Platforms
---

### Post by cdenley on 2011-03-23
How does caching work exactly? I just started reconfiguring apache's mod_expires settings, but I want to completely understand how this will effect the users. I've been trying to read the [HTTP/1.1 docs]("http://www.w3.org/Protocols/rfc2616/rfc2616-sec13.html"), but they're making my head hurt. 

From what I understand, if apache sets the max-age, then the browser will cache that file and not send another GET request until the cached copy becomes older that max-age. However, looking at requests in firebug, this doesn't appear to be the case. Do browsers (Firefox 3) decide what cache-able content to cache and what not to cache?

Also, I noticed that for static content, even without max-age defined (or set really short), it will send a "If-Modified-Since" request header, then the server will give a 304 reply if it hasn't been modified. That request header doesn't seem to be sent for dynamic content. The browser seems to know what html content is static somehow. Does it look for file extensions or something?

It has been suggested to me that the max-age should be greater than 30 days for images, css, js, etc. If changes to these files can take a month to propagate, 30 days seems excessive to me.

---

### Post by falko on 2011-03-23
This might help: [http://gtmetrix.com/leverage-browser-caching.html](http://gtmetrix.com/leverage-browser-caching.html)

> It has been suggested to me that the max-age should be greater than 30 days for images, css, js, etc. If changes to these files can take a month to propagate, 30 days seems excessive to me.That's why you should version your files, e.g. myimage-1.0.0.jpg, myimage-1.0.1.jpg, and so on.

---

### Post by cdenley on 2011-03-24
> **falko said:**
> This might help: [http://gtmetrix.com/leverage-browser-caching.html](http://gtmetrix.com/leverage-browser-caching.html)

That's why you should version your files, e.g. myimage-1.0.0.jpg, myimage-1.0.1.jpg, and so on.

I had considered always renaming a file whenever it is changed, but then you have to make sure you fix all references to the file. If myimage.jpg appears on 20 different pages and I want to make a small change, I shouldn't have to change all 20 references.

Also, that explanation of max-age is how I thought it was supposed to work, but it doesn't seem to match what I actually observe. For example, I browse to the homepage, and the browser downloads a cache-able CSS file:

GET /home.css -> 200: max-age=172800

then, a couple minutes later, well before the cached file is stale, I reload the page:

GET /home.css -> 304: max-age=172800

Why did my browser send another GET request? It used a cache version because it got a 304 response, but I thought setting max-age is supposed to prevent the GET request? Not to mention my browser downloaded that file yesterday, so it should have been cached to begin with. I haven't manually cleared the cache.

---

### Post by SeijiSensei on 2011-03-24
The browser sends a GET request to make sure that the file still has the same timestamp as it did before.  The 304 reply tells it to use the cached copy.  See [http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.3.5](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.3.5).

If you want to understand the details of how caching works, you need to read that RFC.

---

### Post by cdenley on 2011-03-24
> **SeijiSensei said:**
> The browser sends a GET request to make sure that the file still has the same timestamp as it did before.  The 304 reply tells it to use the cached copy.  See [http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.3.5](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.3.5).

If you want to understand the details of how caching works, you need to read that RFC.

I did read that. In fact I linked to it in my first post. The reason why I'm posting here is because what I observe doesn't seem to match my understanding of the RFC. If the expiration hasn't been reached, the file isn't stale, and the browser shouldn't need to revalidate it! The browser can ask the server to compare the server's timestamp to the browser's cached version's timestamp regardless of the expiration age given by the server.

---

### Post by cdenley on 2011-03-24
> **cdenley said:**
> 
Also, I noticed that for static content, even without max-age defined (or set really short), it will send a "If-Modified-Since" request header, then the server will give a 304 reply if it hasn't been modified. That request header doesn't seem to be sent for dynamic content. The browser seems to know what html content is static somehow. Does it look for file extensions or something?


I think I figured out the answer to my own question. The server gives a "Last-Modified" header in all responses for static content. For dynamic content, there is no "Last-Modified" header. This value from when content is cache must be what the browser uses for subsequent requests for the same URL in the "If-Modified-Since" header.

I understand how this heuristic caching works now, but firefox still seems to be treating the max-age value from the server as a suggestion. The browser isn't supposed to revalidate content which hasn't expired, right?

---

### Post by falko on 2011-03-24
Not all clients have support for *max-age*; better use an *Expires* header.

---

### Post by tgalati4 on 2011-03-24
Wow, in many years of forum use, this is the first time I have seen:

RTFRFC

I think part of the issue is evolving frameworks.  Apache versus apache2.  Web 1.0 versus Web 2.0.  There's a lot of legacy configuration variables in the apache config file that may or may not work as intended.  Sometimes they are retained for backward compatibility.  Sometimes they just become obsolete but are never removed.  Changing the default values may have an effect on certain browsers or certain versions of certain browsers.

I'm amazed that any of this stuff works at all.

---

### Post by cdenley on 2011-03-24
> **falko said:**
> Not all clients have support for *max-age*; better use an *Expires* header.

I'm using both since I'm using mod_expires.

---

### Post by cdenley on 2011-03-24
> **tgalati4 said:**
> Wow, in many years of forum use, this is the first time I have seen:

RTFRFC

I think part of the issue is evolving frameworks.  Apache versus apache2.  Web 1.0 versus Web 2.0.  There's a lot of legacy configuration variables in the apache config file that may or may not work as intended.  Sometimes they are retained for backward compatibility.  Sometimes they just become obsolete but are never removed.  Changing the default values may have an effect on certain browsers or certain versions of certain browsers.

I'm amazed that any of this stuff works at all.

I know how it works on the server side. I can see the headers apache puts in the responses. What I can't figure out is how browsers decide when to revalidate.

---

### Post by cdenley on 2011-03-24
I think it actually is working the way I had expected. The source of my confusion was two things:

1. When previously cached fresh items are displayed, firebug displays the headers from the original request when it was cached.

2. Firefox will re-validate on a refresh.

---


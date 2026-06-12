---
title: "Regarding Apache redirection"
date: 2008-10-08
forum: Server Platforms
---

### Post by coolamy55 on 2008-10-08
Greetings ...

I need some help regarding Apache redirection .

Say i have my website hosted on 219.159.117.97 server... under wamp .

Its a PHP forum .

I have registered a domain also [www.example.com](www.example.com)

I have redirected the index.php on [www.example.com](www.example.com) to [http://219.159.117.97/forums](http://219.159.117.97/forums) ....

i want to change the apperaing of Ip add wenever i opens [www.example.com](www.example.com)

waiting for ur reply

rgds

---

### Post by cdenley on 2008-10-08
> **coolamy55 said:**
> Greetings ...

I need some help regarding Apache redirection .

Say i have my website hosted on 219.159.117.97 server... under wamp .

Its a PHP forum .

I have registered a domain also [www.example.com](www.example.com)

I have redirected the index.php on [www.example.com](www.example.com) to [http://219.159.117.97/forums](http://219.159.117.97/forums) ....

i want to change the apperaing of Ip add wenever i opens [www.example.com](www.example.com)

waiting for ur reply

rgds

Why are you redirecting to your IP, then? Why not redirect to [http://www.example.com/forums](http://www.example.com/forums)?

---

### Post by SeanHodges on 2008-10-08
My understanding is that you have 2 hosts:

1) A hosted site, which has the [www.example.com](www.example.com) domain name pointing at it.
2) A server (219.159.#.#) with the PHP forum on it.

You've created an index.php on the hosted site that redirects you to the other server. Obviously this changes the URL in the address bar, so I suspect you are looking for a way to mask the fact the PHP forum is on another machine?

The way I see it is you have 2 options. The cleanest would be to just change your domain name to point at the other server, and just ditch the whole idea of redirecting between the 2 hosts. You haven't indicated any reason why you'd need this set-up anyway.

The second option would be to look into Apache's mod_rewrite module, which should allow you to Alias [www.example.com/forums](www.example.com/forums) to the other server without losing the address. This would require a bit of effort, but I think it should be possible.

---

### Post by cdenley on 2008-10-08
> **SeanHodges said:**
> My understanding is that you have 2 hosts:

1) A hosted site, which has the [www.example.com](www.example.com) domain name pointing at it.
2) A server (219.159.#.#) with the PHP forum on it.

You've created an index.php on the hosted site that redirects you to the other server. Obviously this changes the URL in the address bar, so I suspect you are looking for a way to mask the fact the PHP forum is on another machine?

The way I see it is you have 2 options. The cleanest would be to just change your domain name to point at the other server, and just ditch the whole idea of redirecting between the 2 hosts. You haven't indicated any reason why you'd need this set-up anyway.

The second option would be to look into Apache's mod_rewrite module, which should allow you to Alias [www.example.com/forums](www.example.com/forums) to the other server without losing the address. This would require a bit of effort, but I think it should be possible.

I think mod_rewrite would also redirect, changing the URL in the browser. You would need to use mod_proxy, so the [www.example.com](www.example.com) server will send a web request to 219.159.117.97, and display the result to the client. The client wouldn't even be able to tell that the server 219.159.117.97 is involved in the process. If the [www.example.com](www.example.com) server has limited bandwidth, though, this will create a bottleneck.

You could make a frames page for [www.example.com](www.example.com), then put 219.159.117.97 in a frame that uses the entire window. I always found this trick really annoying, though.

---

### Post by tehlaser on 2008-10-08
If I understand you correctly, you want to forward requests to /forums to another webserver, but you don't want this showing up in the browser; you want it to look like they're both on the same server.

If so, what you're looking for is mod_proxy.  In short, you need to make sure mod_proxy and mod_proxy_http are loaded (run something like "sudo a2enmod proxy" to do this), then add this to your apache config:

```
ProxyPass /forums http://219.159.#.#
```

---

### Post by SeanHodges on 2008-10-08
> **cdenley said:**
> I think mod_rewrite would also redirect, changing the URL in the browser. You would need to use mod_proxy

You're right of course, my mind was thinking mod_proxy, but my fingers were on their own little mission ;)

---


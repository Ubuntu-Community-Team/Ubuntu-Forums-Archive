---
title: "Squid doesn't block sites"
date: 2008-01-10
forum: Server Platforms
---

### Post by KarateCowboy on 2008-01-10
'aight so running 7.10 and fresh install.  have squid straight from the box except in the config i set my visible_hostname.

I added these lines 
```

acl bad url_regex "/etc/squid/squid-block.acl"
http_access deny bad

```

and have the file squid-block.acl in that spot with permissions 755.
I tested it to see if it would keep me from going to yahoo.com by just putting the word 'yahoo' in there with no quotes and restarted squid with
```

sudo /etc/init.d/squid restart

```
and all seemed fine.
But then I loaded up firefox and went to yahoo.com and I can read all the latest news.  What am I missing i wonder.  Do those lines need to go in a specific spot in the file or what?

---

### Post by koenn on 2008-01-10
is firefox configured to use a proxy or is it connecting directly to the internet ?

---

### Post by KarateCowboy on 2008-01-10
It's connecting directly.  Does it need to be specified?  It just seems kind of pointless to have a proxy if a user can just go and change that setting and get around it.

Anyway, it's connecting directly.

---

### Post by KarateCowboy on 2008-01-10
Right so I set firefox to manual proxy specification.

HTTP Proxy 127.0.0.1 port 3128

Socks 5

no proxy for: localhost, 127.0.0.1
No deal,. still doesn't work

---

### Post by koenn on 2008-01-10
> It's connecting directly. Does it need to be specified? It just seems kind of pointless to have a proxy if a user can just go and change that setting and get around it.

you can't really expect squid to block connections that it can't see and know nothing about, can you ?
so yes, it matters, and you have to make things so that browsers use the proxy, if you want to use them for browsing. 

There's a couple of ways to do that
you can setup for transparent proxy. This involves some changes in squid.conf and configuring a router or iptables to redirect port 80 (http) to port 3128 (proxy)

You can also lock firefox preferences by editing
 /usr/share/firefox/greprefs/all.js and
 /usr/lib/firefox/firefox.cfg

you could possibly combine this with proxy auto detection

here's some reading material :
[http://users.telenet.be/mydotcom/howto/linuxkiosk/webterm02.htm](http://users.telenet.be/mydotcom/howto/linuxkiosk/webterm02.htm)
[http://users.telenet.be/mydotcom/library/network/pac.htm](http://users.telenet.be/mydotcom/library/network/pac.htm)

---

### Post by koenn on 2008-01-10
you're running squid and firefox on the same computer ?

---

### Post by KarateCowboy on 2008-01-10
Yes.
This is an home PC.  I would like to block bad sites because I have kids.  This is what all the sites out there are telling me to do.
I was following these directions
[http://www.freesoftwaremagazine.com/articles/web_blocking_squid/](http://www.freesoftwaremagazine.com/articles/web_blocking_squid/)

---

### Post by koenn on 2008-01-10
search on these forums and other ubuntu docs for 'dansguardian' -
that's a proxy + content filtering preconfigured, and I've seen some howto's around.
you can also get it from Ubuntu Cristian Edition website

---

### Post by KarateCowboy on 2008-01-10
ok thanks

---

### Post by koenn on 2008-01-10
this looks like a good start
[http://ubuntuforums.org/showthread.php?t=207008](http://ubuntuforums.org/showthread.php?t=207008)

---

### Post by zeronothing on 2008-01-10
to use squid to block websites and not have to specify a proxy in your browser, you have to enable transparent proxy. Their is more to it than me just saying enabling a configuration. It would also depend on you home network setup. It is possible to not have to specify a proxy server in your web browser, in order to block websites.

---


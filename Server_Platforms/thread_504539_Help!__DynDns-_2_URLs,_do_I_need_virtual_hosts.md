---
title: "Help!  DynDns- 2 URLs, do I need virtual hosts?"
date: 2007-07-19
forum: Server Platforms
---

### Post by capnbenzo on 2007-07-19
Hey Everyone,

I have a problem which I can't seem to find in the older posts.

I set up Apache2 with Dynamic DNS from dyndns.org at xxxxx.kicks-***.net.  This page loads fine.

I also set up Custom DNS from dyndns.org (also dynamic) so I could point [www.myurl.com](www.myurl.com) to this server as well.  This URL is generating a server not found error.

So, both URLs point to the same IP, but only one loads.  I checked with dyndns and everything is ok on their end: DNS updated, my router is forwarded right.

The only thing I can think of is that I might need to change my Apache2 config somehow- maybe virtual hosts?  Is that true?  Just to be clear, both URLs point to the SAME IP and should be the same web page.

Thanks!

---

### Post by capnbenzo on 2007-07-19
UPDATE


I added the following to my httpd.conf

 NameVirtualHost myip

<VirtualHost myip>
ServerName [www.myurl.com](www.myurl.com)
ServerAlias myurl.com *.myurl.com
DocumentRoot /var/www/
</VirtualHost>

<VirtualHost myip>
ServerName xxxxx.kicks-***.net
DocumentRoot /var/www
</VirtualHost>


Still same issue.  xxxxx.kicks-***.net works, but [www.myurl.com](www.myurl.com) times out.

:(


Thanks!

---

### Post by MJN on 2007-07-19
If you gave us the real domains we could rule out DNS issues immediately and pinpoint it down to an Apache issue. Hiding these domains provides arguably no security benefit yet makes troubleshooting that much more difficult.
 
PM them to me (or anyone else that joins the thread) if you'd prefer.
 
Mathew

---

### Post by MJN on 2007-07-19
As an aside, I just spotted you've got a trailing slash on that first DocumentRoot. Furthermore, there's no need for two sections given all names are for the same site hence try the following:
 
```

NameVirtualHost *:80
 
<VirtualHost *>
ServerName [_[COLOR=#0000ff]www.myurl.com[/COLOR]_]("http://www.myurl.com/")
ServerAlias myurl.com *.myurl.com xxxxx.kicks-***.net
DocumentRoot /var/www
</VirtualHost>

```
 
Mathew

---

### Post by capnbenzo on 2007-07-19
Thanks guys!  I found my router had reassigned local IPs.  

Sorry for the trouble!

---

### Post by MJN on 2007-07-19
I don't understand what you meant, but glad you got it sorted either way!
 
Mathew

---


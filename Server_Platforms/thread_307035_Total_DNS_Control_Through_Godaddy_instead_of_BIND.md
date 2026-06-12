---
title: "Total DNS Control Through Godaddy instead of BIND?"
date: 2006-11-26
forum: Server Platforms
---

### Post by luckylucky on 2006-11-26
Hi Server gurus,

I have an off the wall question regarding servers here...  rather than setting up BIND on my server could I use the "Total DNS Control and MX Records" service through Godaddy, somehow pointing the info at my server via it's IP address and get virtualHost working in Apache without having to go through the trouble (aka confusion) of setting up BIND?  Alternately do sites like easydns.com work in what I'm alluding to here?  Bottom line is can I make this work easily, and would this work well, or am I completely going in the wrong direction?

Thanks for any feedback!  :)

---

### Post by Kurt` on 2006-11-26
The Total DNS Control thing allows you to specify nameservers.

Requests sent for anything on your domain get passed along to the nameservers specified, and the DNS daemon on said nameservers tell the client which A/AAA/etc. records point to which IP addresses...

Unless the Total DNS Control thing is different now, last I checked it only allowed you to specify 2 or more nameservers.

---

### Post by MJN on 2006-11-26
GoDaddy does support full control of the DNS for your domain so, yes, you can do what you want and as you say this may make sense for you if only so you've got one less thing (BIND) to learn! ;)

[http://help.godaddy.com/article.php?article_id=682&topic_id=163&&](http://help.godaddy.com/article.php?article_id=682&topic_id=163&&)
[http://help.godaddy.com/article.php?article_id=671&topic_id=163&&](http://help.godaddy.com/article.php?article_id=671&topic_id=163&&)

Mathew

---

### Post by Kurt` on 2006-11-26
Bind isn't really that difficult, but whatever is easiest! :)

---

### Post by MJN on 2006-11-26
Well, no, but that's beside the point - there's no point using it if you don't need/want to particularly as the OP has got a good-to-go solution from his domain provider.

Mathew

---


---
title: "How to forward all web traffic from one server to another"
date: 2011-06-02
forum: Server Platforms
---

### Post by showe1966 on 2011-06-02
Heres a freaky problem for you cats.
My kind isp had set up a authoratitive dns server that can't be cancelled that points to the wrong ip address.

Hence I need to take all the traffic going into server A at the ip address aa.aa.aa.aa and send it all onto server B at ip address bb.bb.bb.bb.

After much head scratching, I managed to achieve it as follows:-

On the server at ip address A, set up following :-

iptables -t nat -A PREROUTING -d aa.aa.aa.aa -j DNAT --to bb.bb.bb.bb
iptables -t nat -A POSTROUTING -d bb.bb.bb.bb -j MASQUERADE

Argg my brain is burning out...

---

### Post by ruffEdgz on 2011-06-02
I don't know if you just have a basic apache installed on address A but if you did, you could have redirected the traffic that way as well:

Resource: [http://httpd.apache.org/docs/2.0/mod/mod_alias.html#redirect](http://httpd.apache.org/docs/2.0/mod/mod_alias.html#redirect)

```

Redirect permanent /service http://addressd/service

```

And another way would be through your index.html/index.php page on your address A server place this code in there:

```

<meta http-equiv="refresh" content=0;URL=http://addressb/service>

```

The last one isn't that great and will not notify others about your new location but it works.

Cheers!

---


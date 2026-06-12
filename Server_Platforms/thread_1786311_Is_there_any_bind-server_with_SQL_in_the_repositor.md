---
title: "Is there any bind-server with SQL in the repositories ?"
date: 2011-06-19
forum: Server Platforms
---

### Post by WitchCraft on 2011-06-19
I need a bind-server (I mean DNS server) with a SQL backend.
As far as I have seen, the only viable option I have is to recompile bind9 with support for either MySQL or PostGre.

Link to this:
[http://diaryproducts.net/about/operating_systems/unix/installing_bind9_with_dlz_and_mysql_backend_on_ubuntu_jaunty_9_04](http://diaryproducts.net/about/operating_systems/unix/installing_bind9_with_dlz_and_mysql_backend_on_ubuntu_jaunty_9_04)
with an additional 
```

apt-get install libpqxx3-dev 

```

From some tutorials I have read, I see I need to recompile it to enable its SQL support.

But when I do it that way, I won't get any security updates, won't  I?

So... Is there any bind server with SQL support in the repositories ? For that I don't have to worry about security updates...

---

### Post by BkkBonanza on 2011-06-20
There is **powerdns** - it has an optional mysql backend. I'm not a big fan but I did test it out once and it worked ok. I didn't really like it because it sucked about 75MB of RAM. And I wasn't impressed by their community being almost catatonic.

I ended up using TinyDNS (djbdns) and was happy with that only taking 1-2 MB of RAM. It has a mysql converter tool that can update it's native data file from a mysql database (atomically).

Still, I would likely choose powerdns over bind, which in my djb influenced opinion is crap.

---


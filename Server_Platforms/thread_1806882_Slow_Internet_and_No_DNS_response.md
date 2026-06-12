---
title: "Slow Internet and No DNS response"
date: 2011-07-18
forum: Server Platforms
---

### Post by yokobr on 2011-07-18
Hi guys,
I have an Ubuntu 10.04 server here, and this week internet sharing got too slow... i dunno if it is a squid problem... but it's too slow. And when i try to registar a domain for that server, bind gives do response. If i dig my server inside lan, it's working pretty well. 
Sorry for my bad english

---

### Post by terazen on 2011-07-18
Can you give an example of what you mean by this?

"And when i try to registar a domain for that server, bind gives do response."

---

### Post by ruffEdgz on 2011-07-18
> **terazen said:**
> Can you give an example of what you mean by this?

"And when i try to registar a domain for that server, bind gives do response."

To go off this, can you ping the DNS ip that is found in your resolv.conf file?
```

cat /etc/resolv.conf | grep nameserver | awk '{print $2}' | while read line; do ping -c4 $line; done

```
Just sounds like your resolv.conf doesn't have the correct DNS or something up that ally.

---


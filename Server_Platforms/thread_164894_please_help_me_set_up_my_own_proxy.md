---
title: "please help me set up my own proxy"
date: 2006-04-23
forum: Server Platforms
---

### Post by brendanross on 2006-04-23
I want to set up a proxy through my home ubuntu computer so I can use it at school from their computers to view blocked web sites. How do I do this?

---

### Post by fdoving on 2006-04-24
```

sudo apt-get install squid

```

Edit /etc/squid/squid.conf to allow school ip's to connect to the proxy. You can also setup authentication.

- Frode

---

### Post by brendanross on 2006-04-25
[QUOTE=fdoving]```

sudo apt-get install squid

```

Edit /etc/squid/squid.conf to allow school ip's to connect to the proxy. You can also setup authentication.

- Frode[/QUOTE]
thank you so much!!

---

### Post by brendanross on 2006-04-25
[QUOTE=fdoving]```

sudo apt-get install squid

```

Edit /etc/squid/squid.conf to allow school ip's to connect to the proxy. You can also setup authentication.

- Frode[/QUOTE]
where do I allow my school's ip address in that file?

---

### Post by fdoving on 2006-04-26
Search for 'acl' (Access control list.)


- Frode

---

### Post by fdoving on 2006-04-26
ops.. doubleposted.

---


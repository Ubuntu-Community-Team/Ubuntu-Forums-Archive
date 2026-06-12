---
title: "freeradius problems"
date: 2011-06-11
forum: Server Platforms
---

### Post by cryptoboss on 2011-06-11
Hi everybody I configured the server freeradius with mysql and I think I configured well freeradius and mysql but when I m testing my configuration with : 

radtest nezar azerty 127.0.0.1 0 azerty1234

I have always :

rad_recv: Access-Reject packet from host 127.0.0.1 port 1812, id=108, length=20

but I dont know where is the probleme ?

help me please.

---

### Post by eldoradol on 2011-08-26
```
 radtest nezar azerty 127.0.0.1 0 azerty1234
```change to :

```

radtest root rootpasswd 127.0.0.1 0 mysecret

```[COLOR=green]rad_recv: **Access-Accept** packet from host 127.0.0.1:1812, id=34, length=20[/COLOR]

---


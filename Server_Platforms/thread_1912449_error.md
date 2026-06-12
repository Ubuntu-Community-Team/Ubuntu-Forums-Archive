---
title: "error"
date: 2012-01-20
forum: Server Platforms
---

### Post by san_tiago23 on 2012-01-20
Como puedo solucionar el siguiente error, al momento de querer ingresar a mi plataforma me sale este error [http://1.1](http://1.1) internal service       error 11
Tengo instalado unbuntu con apache

---

### Post by rubylaser on 2012-01-20
I don't speak Spanish, but the ip address that you're typing in is not a correct ip.  If you're trying to reach the localhost, you'd need to use [http://127.0.0.1]("http://127.0.0.1") and if you're trying to connect to it from another machine, you'd need to use it's ipaddress, which you can get like this.

```
ifconfig eth0 | grep 'inet addr:' | cut -d: -f2 | awk '{ print $1}'
```

I'm not sure that's what you're asking, but I hope it helps.

---

### Post by CharlesA on 2012-01-20
Threw the OP at google translate and it spit this back out:

> As I can solve the following error when wanting to access my platform [http://1.1](http://1.1) I get this error error 11 internal service
I have installed unbuntu with apache

Ruby hit it spot on. You can access it via [http://localhost](http://localhost) as well.

---


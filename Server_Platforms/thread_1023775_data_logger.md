---
title: "data logger"
date: 2008-12-28
forum: Server Platforms
---

### Post by herrbrand on 2008-12-28
hello

i seek a good logging program. i want to see easy al activities on my server. complete with IP adresses. is there a program like that?

Robbert

---

### Post by Dr Small on 2008-12-28
Data logging for what?
You already have /var/log/auth.log

---

### Post by ushimitsudoki on 2008-12-28
> **herrbrand said:**
> hello

i seek a good logging program. i want to see easy al activities on my server. complete with IP adresses. is there a program like that?

Robbert

I like [ntop]("http://www.ntop.org") - give it a look and see if it meets your needs.

---

### Post by HermanAB on 2008-12-28
$ sudo tail -f /var/log/messages

---


---
title: "eximconfig doesn't exist"
date: 2009-04-09
forum: Server Platforms
---

### Post by jdcnosse on 2009-04-09
So I was going to install exim4, and I was using [this howto]("http://newbiedoc.sourceforge.net/networking/exim.html") to help me configure exim correctly, and it references eximconfig, but when I type that into the terminal it comes up as command not found...

---

### Post by brian_p on 2009-04-10
> **jdcnosse said:**
> 

So I was going to install exim4, and I was using [this howto]("http://newbiedoc.sourceforge.net/networking/exim.html") to help me configure exim correctly, and it references eximconfig, . . . . 

Which was for exim3.

>  . . . . .  but when I type that into the terminal it comes up as command not found...

```
dpkg-reconfigure exim4-config
```

---

### Post by jdcnosse on 2009-04-11
ooh...okiedokie thanks for the exim4 config code.

---


---
title: "How to find my Apache version on Ubuntu server"
date: 2009-08-20
forum: Server Platforms
---

### Post by jocampo on 2009-08-20
This is a newbie question but I've searched for like 1 hour, and most online resources point to

```

httpd -v

```

But! that command just does not work on my Ubuntu server. In fact, I can not even find a service with such name; it looks like such command works on Red Hat or other distros, not Ubuntu. How do I suppose to find the Apache version?

Just playing around I was able to get the information doing this by myself

```
/usr/sbin/apache2ctl status | grep Version

```

but that's kind of a workaround I guess, more than a real command...

BTW, mine is 2.2.11

---

### Post by Thirtysixway on 2009-08-20
```

apache2 -v

```

---

### Post by jocampo on 2009-08-20
Thanks a lot!!!!

---


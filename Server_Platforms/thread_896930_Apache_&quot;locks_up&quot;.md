---
title: "Apache &quot;locks up&quot;"
date: 2008-08-21
forum: Server Platforms
---

### Post by allspiritseve on 2008-08-21
Hello all,

I have a VERY annoying bug going on with my local apache server I have set up. Every once in a while, I'll be editing a file, and when I click refresh, nothing will change. It's like it's cached the file on the server, and isn't updating a new copy. I have no idea why it's doing this, and reloading apache doesn't help. Once in a while, if I wait a bit and hit refresh, it will update. Anyone know how to fix this?

Thanks,

Cory

---

### Post by cdenley on 2008-08-21
Are you sure it's not your browser doing the caching. Use wget or telnet to see if the wrong version is actually being sent by the server.
```

telnet mydomain.com 80
GET /myfile.php HTTP/1.0


```
(last line is blank)

By the way, that title is very misleading. If it were "locked up" the server wouldn't be giving any response at all.

---

### Post by allspiritseve on 2008-08-23
It was my browser. Thanks for your help.

---


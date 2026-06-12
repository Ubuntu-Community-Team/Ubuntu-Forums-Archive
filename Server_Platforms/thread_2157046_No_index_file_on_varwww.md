---
title: "No index file on /var/www"
date: 2013-06-24
forum: Server Platforms
---

### Post by alfirdaous on 2013-06-24
Hello everybody,

I installed apache2 on ubuntu 12, there was no index file created while installing apache2, thanks for your help

---

### Post by Lars Noodén on 2013-06-24
You could try reinstalling Apache2

```

sudo apt-get --reinstall install apache2

```

Or you could make your own index.html file using tidy, bluefish or bluegriffon.

---

### Post by alfirdaous on 2013-06-24
That's because of what even I reinstall apache2, still remain the same problem

---

### Post by newbie-user on 2013-06-24
Here you go. Just copy & paste into your own index.html:
```

<html><body><h1>It works!</h1>
<p>This is the default web page for this server.</p>
<p>The web server software is running but no content has been added, yet.</p>
</body></html>

```

---

### Post by alfirdaous on 2013-06-25
Thanks for that

---

### Post by CharlesA on 2013-06-25
> **Lars Noodén said:**
> You could try reinstalling Apache2

```

sudo apt-get --reinstall install apache2

```

Or you could make your own index.html file using tidy, bluefish or bluegriffon.

I remember accidentally deleting index.html or /var/www and having to reinstall apache2-common to get it back. Dunno if that works in this case, but it's really easy to recreate the index.html test page as newbie-user has done.

---

### Post by alfirdaous on 2013-06-25
thanks for the info

---


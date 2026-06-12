---
title: "CLI apt repo search"
date: 2009-04-28
forum: Server Platforms
---

### Post by theox26 on 2009-04-28
Is there a way to search the repositories from the command line?
I have a server install and it's getting annoying looking online on another computer to find the package names.

I've look all over and haven't found a way to do it.

Thanks

---

### Post by _Purple_ on 2009-04-28
```
apt-cache search <packagename>
```

---

### Post by theox26 on 2009-04-28
Thank you so much.  You have made my life much easier as I do this server install.

---

### Post by _Purple_ on 2009-04-28
My pleasure :)

---

### Post by sirjoebob on 2009-04-28
You can also do either of these:

> aptitude search NAME
> aptitude search -d DESCRIPTION

---


---
title: "Browse the web with Ubuntu server edition?"
date: 2010-04-21
forum: Server Platforms
---

### Post by TheAlien on 2010-04-21
I'd like to setup a webserver with the Ubuntu server edition. But I'd like to browse the web with it too, but only with a really simple browser. Is that possible without installing a desktop environment?

---

### Post by Bachstelze on 2010-04-21
There is a good number of command-line Web browsers available. My personal favourite is links.

---

### Post by wojox on 2010-04-21
And w3m is installed by default.

```
w3m -v http://www.google.com
```

---

### Post by Bachstelze on 2010-04-21
> **wojox said:**
> And w3m is installed by default.

```
w3m -v http://www.google.com
```

Is it? I don't have it here, and I don't remember uninstalling it.

---

### Post by iissmart on 2010-04-22
I use lynx, it's pretty much the same thing as links or elinks.

---

### Post by arrrghhh on 2010-04-22
> **iissmart said:**
> I use lynx, it's pretty much the same thing as links or elinks.

I second lynx, but I don't ever browse the web via the console.  I have needed to before, and lynx was awesome.

---

### Post by Iowan on 2010-04-22
I have **elinks** on my LAMP server - interesting challenge to use...

---

### Post by TheAlien on 2010-04-23
> **wojox said:**
> And w3m is installed by default.

```
w3m -v http://www.google.com
```

Thanks, that was exactly what I needed!

Another question: How does w3m handle scripts, Java, Cookies and etc?

---


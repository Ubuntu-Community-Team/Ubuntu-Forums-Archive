---
title: "is X then only difference?"
date: 2009-11-22
forum: Server Platforms
---

### Post by oospill on 2009-11-22
could I setup X to run on an Ubuntu Server at startup and make it be *just* like Ubuntu Desktop??

what's the difference?

AND -- can I run server-type services on my Desktop installation?

thanks!!

---

### Post by Vegan on 2009-11-22
The default desktop run on top of x, as for server services, you can run them, you will have to read the manuals for servers though as they are a bit of work to setup.

---

### Post by oospill on 2009-11-25
so if one were to list them, what are the differences between Ubuntu Desktop & Ubuntu Server?

thanks

---

### Post by Finland_Penguin on 2009-11-25
> **oospill said:**
> so if one were to list them, what are the differences between Ubuntu Desktop & Ubuntu Server?

thanks

Ubuntu server has no x and comes with server software and tools.

---

### Post by oospill on 2009-11-25
okay I'll take that.  sounds kinda vague at first.  but I guess that's all there is to it.  thanks

---

### Post by stefanadelbert on 2009-11-25
It's possible to install a package on top of an Ubuntu Server installation to "turn it into" Ubuntu Desktop:

```
sudo apt-get ubuntu-desktop
```

The package is described [here]("http://packages.ubuntu.com/dapper/ubuntu-desktop") and basically comprises X, gnome and a bunch of desktop apps.

You can do something similar with xfce. BlackBox is a nice, lightweight windows manager and might be worth looking into.

---


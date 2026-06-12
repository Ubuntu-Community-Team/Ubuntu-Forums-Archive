---
title: "Curiosity: difference between Hardy desktop and server"
date: 2008-09-24
forum: Server Platforms
---

### Post by stek79 on 2008-09-24
Hello guys,
    I was wondering about the difference between the desktop and server version.

In particular, since the two versions have different support lifespan, what are the differences in terms of packages?

Don't they share the same repository?

If not, what are the packages supported for 5 years?

If from a server distro I want to have a GUI to ease administration tasks, can I install the package ubuntu-desktop? Or there are some appropriate GUI tools?

Thanks in advance

---

### Post by cdenley on 2008-09-24
[http://www.ubuntu.com/products/whatisubuntu/serveredition/techspecs](http://www.ubuntu.com/products/whatisubuntu/serveredition/techspecs)

I guess only the packages commonly used on servers will be maintained in the hardy repo after 3 years and desktop-related stuff won't be updated or fixed after that. I would imagine that security updates would still be backported, though. 

The server and desktop installs both share the same repo, though, and you can select any ubuntu configuration you want after the install.
```

sudo tasksel

```

---

### Post by windependence on 2008-09-24
[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel)

-Tim

---

### Post by cdenley on 2008-09-24
> **windependence said:**
> [http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel)

-Tim

To install the desktop kernel
```

sudo apt-get install linux-generic

```

To install the server kernel
```

sudo apt-get install linux-server

```

---

### Post by steve_c on 2008-09-24
Just cause I'm curious, what's the difference between doing a:
sudo tasksel
and selecting server from a Hardy desktop and doing a:
sudo aptitude install linux-server

Are they different syntax for the same thing, or does tasksel do something more than just change the kernel?

Thanks for this thread. I've been curious about this for a while.

---

### Post by cdenley on 2008-09-24
> **steve_c said:**
> Just cause I'm curious, what's the difference between doing a:
sudo tasksel
and selecting server from a Hardy desktop and doing a:
sudo aptitude install linux-server

Are they different syntax for the same thing, or does tasksel do something more than just change the kernel?

Thanks for this thread. I've been curious about this for a while.

tasksel will allow you to choose server configurations which you normally select during a server install, among other configurations. You can choose between mail, LAMP, etc. Installing the linux-server package will only install the server optimized kernel. It will not install any server software.

---


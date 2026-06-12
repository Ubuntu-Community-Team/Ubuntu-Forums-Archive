---
title: "[SOLVED] &amp;quot;make&amp;quot; not installed by default"
date: 2008-06-14
forum: Server Platforms
---

### Post by Richard_ on 2008-06-14
Hi everyone.

Being kinda very new here, I hope I'm posting in the right section. O:)

I've just installed Ubuntu Server 8.04, and I've noticed that "make" isn't installed by default, and neither is compiler gcc. I easily downloaded them with apt-get, but my curiosity is still peaked as to why both these important utilities aren't shipped with Ubuntu Server 8.04?

---

### Post by Dr Small on 2008-06-14
To save on bloat, I guess. But it would make sense to have this stuff pre-installed on the server edition, in case you wanted to do some (or had to do some) compiling before you got online with it.

The simple way to install the lot of it is:
```
sudo apt-get install build-essential
```

Dr Small

---

### Post by logos34 on 2008-06-14
oddly enough, build-essential is even included on the installation cd, but it doesn't install by default.  I have never understood why

---

### Post by dendrobates on 2008-06-14
It is left off because of more than bloat.  Remember, Ubuntu server is designed for production environments. It is best in most cases not to be able to build binaries on your production servers.  It is fine to add it if you need it, but since it raises the risk profile of the server it should not be installed by default.

Rick

Manager, Ubuntu Server Team

---

### Post by logos34 on 2008-06-15
> **dendrobates said:**
> It is left off because of more than bloat.  Remember, Ubuntu server is designed for production environments. It is best in most cases not to be able to build binaries on your production servers.  It is fine to add it if you need it, but since it raises the risk profile of the server it should not be installed by default.

Interesting. That makes sense.  

But why not on the regular desktop install cd?  I guess that's really what I had in mind (I now realize this is the server forum)

---

### Post by pdwerryhouse on 2008-06-15
> **logos34 said:**
> But why not on the regular desktop install cd?

The average desktop user wouldn't really need to compile anything either; anyone who needs to do so, probably has enough knowledge about the system to be able to do it themselves.

Cheers,

Paul

---

### Post by windependence on 2008-06-15
> **dendrobates said:**
> It is left off because of more than bloat.  Remember, Ubuntu server is designed for production environments. It is best in most cases not to be able to build binaries on your production servers.  It is fine to add it if you need it, but since it raises the risk profile of the server it should not be installed by default.

Rick

Manager, Ubuntu Server Team

I am aware they do this for security, but it is really not much of a deterrent. If someone compromises your server, they will most likely be able to load binaries and compilers as well. 

I load the full dev package on my servers and after I have everything set up I remove it if I am still paranoid. Many times I just leave it in place.

-Tim

---

### Post by logos34 on 2008-06-15
> **pdwerryhouse said:**
> The average desktop user wouldn't really need to compile anything either; anyone who needs to do so, probably has enough knowledge about the system to be able to do it themselves.


then why all the threads about failed ./configure, the resolution to which all too often is that they need to install build-essential, make or gcc?  A lot of unnecessary confusion and redundant posts could be prevented by just installing that one pkg by default! I just don't get it

---

### Post by Richard_ on 2008-06-17
Thanks, dendrobates' answer is great. Thanks to everyone else for the insight.  :)

---


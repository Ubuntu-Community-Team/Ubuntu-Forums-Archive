---
title: "[SOLVED] dont want apache and mysql on startup"
date: 2008-03-29
forum: Server Platforms
---

### Post by larsdk on 2008-03-29
Hi there,

I have a LAMP setup, but I only use it every now and then, so I don't want it to startup automatically. How do I change that?

Lars

---

### Post by faulkes on 2008-03-29
> **larsdk said:**
> Hi there,

I have a LAMP setup, but I only use it every now and then, so I don't want it to startup automatically. How do I change that?

Lars

In each for the /etc/rcX.d directories (where X is a run-level number)
find the S<number>mysql and S<number>apache2 symbolic links.

Rename these from S<number>mysql & S<number>apache2 to
K<number>mysql & K<number>apache2.

That will prevent the services from starting automatically and you
can then manually run the /etc/init.d commands to start them
when needed.

Thanks,

Faulkes

---

### Post by Thanoulis on 2008-03-29
You can also install sysv-rc-conf
```
sudo apt-get install sysv-rc-conf
```
It's a ncurces application to manage your daemons...
Make sure to run it with sudo, and read the instructions carefully...it can be deadly...

---

### Post by larsdk on 2008-03-29
I can see that I have 

rc0.d to rc6.d 

which one of them should I go for?

---

### Post by faulkes on 2008-03-29
> **larsdk said:**
> I can see that I have 

rc0.d to rc6.d 

which one of them should I go for?

Any place where those S<number>mysql and S<number>apache2
files exist in any of the rc0.d to rc6.d directories, as each of those
represents a run-level where an application can be told to start.

Thanks,

Faulkes

---


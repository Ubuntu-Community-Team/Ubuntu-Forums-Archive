---
title: "excellent site with preconfigured ubuntu installs for vmware"
date: 2009-01-07
forum: Virtualisation
---

### Post by lex1 on 2009-01-07
This site rocks as it has not only preconfigured installs for ubuntu installing in vmware player and workstation.
Its even got the next release of ubuntu 9.04 a2
and KDE 4.0

take a look here
[http://bagside.com/bagvapp/](http://bagside.com/bagvapp/)


lex1:popcorn:

---

### Post by dbqp on 2009-01-07
Thanks for the link! I think I'll be trying some of these out tonight!

---

### Post by macewan on 2009-01-17
Testing it now - thanks.

---

### Post by dcstar on 2009-01-20
If you want to run these VMs on VMWare server 1.0.x, you have to change to the following in the .vmx file:

```
virtualHW.version = "4"
```

I had to do this with the Ubuntu 9.04 Alpha VM.

---

### Post by dbqp on 2009-07-10
> If you want to run these VMs on VMWare server 1.0.x, you have to change to the following in the .vmx file:

Code:

virtualHW.version = "4"

I had to do this with the Ubuntu 9.04 Alpha VM. 

What if you are running VM Ware Server 2.0?

---


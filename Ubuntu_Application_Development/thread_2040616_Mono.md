---
title: "Mono"
date: 2012-08-11
forum: Ubuntu Application Development
---

### Post by ozooo on 2012-08-11
Hi, 

I'm trying to install mono/monodevelop on my 12.04 but it's not working, monodevelop says that I don't have the nunit framework. The problem is that I do have the nunit framework for CLI installed but it seems that monodevelop doesn't see it. Does anyone know what are the steps to follow to make it working.

Thanks a lot for you help

---

### Post by Lyfang on 2012-08-11
Post the output of the following command(s):
```
sudo apt-get update && sudo apt-get -s install monodevelop-nunit monodevelop 
```

---

### Post by ozooo on 2012-08-11
Thanks Lyfang,

I've found a solution, I changed the target framework of my project from .Net 3.5 to .Net 4.0 and now it works... Now I have to understand why :)

---

### Post by directhex on 2012-08-12
> **ozooo said:**
> Thanks Lyfang,

I've found a solution, I changed the target framework of my project from .Net 3.5 to .Net 4.0 and now it works... Now I have to understand why :)

.NET 4.0 is the only supported version in Ubuntu 11.10 and higher - all libraries on the system are built only for 4.0

---


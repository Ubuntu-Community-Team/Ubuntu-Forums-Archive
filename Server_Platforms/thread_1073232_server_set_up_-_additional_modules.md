---
title: "server set up - additional modules"
date: 2009-02-18
forum: Server Platforms
---

### Post by Mr.Carramba on 2009-02-18
hi,

I'm setting upp new server with dual xeon-quad with ubuntu 8.10_64.
My question is do I need to install aditional modules to get better support for 8 cores?

I will beusing some virtualization software (maybe virtualbox or vmware), do I need any extra modules to enable better performance?

---

### Post by veloce on 2009-02-24
> **Mr.Carramba said:**
> hi,

I'm setting upp new server with dual xeon-quad with ubuntu 8.10_64.
My question is do I need to install aditional modules to get better support for 8 cores?

I will beusing some virtualization software (maybe virtualbox or vmware), do I need any extra modules to enable better performance?

Provided you are running the SMP kernel - check with:

```
uname -a
```

You will get the full benefit of your multiple cores.  Virtualisation is fabulous with multiple cores.  VMWare breaks up the demands of my "single processor" xp vms and spreads them over the 4 processors I have available.  Works very nicely.

---


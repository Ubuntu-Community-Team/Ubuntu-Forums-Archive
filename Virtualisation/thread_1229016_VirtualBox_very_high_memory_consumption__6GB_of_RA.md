---
title: "VirtualBox very high memory consumption : 6GB of RAM used!"
date: 2009-08-01
forum: Virtualisation
---

### Post by kal on 2009-08-01
Hi everybody,

First of all, here is my config : Intel Core i7 920 with 6 GB DDR3 triple channel.

I use Ubuntu 9.04 x64 to get all my ram usable. 

When I try to install Windows 7 through VirtualBox or Vmware Worksation, I get all RAM consumed. Though I define the memory avalaible to guest to 1024 mb!
[[IMG]http://img29.imageshack.us/img29/4649/virtualbox.th.png[/IMG]](http://img29.imageshack.us/i/virtualbox.png/)

Is that ok? My memory consumption shouldn't go over 2/3 GB. But 6 GB is just too much :o

Cheers,
Kal

---

### Post by jocampo on 2009-08-01
HI Kal

hmm...why you say is VirtualBox? try this ...

```
ps -fe|grep VB
```

to get the VirtualBox PID

Once you get that, do this

```
top -p 1234
```

please replace 1234 for the real PID that you previously found. Also, when you run

Finally, during installation. VMs use more resources than normal. Once done, CPU and RAM should go down a bit.

---

### Post by insane_alien on 2009-08-01
your RAM is being filled up by cache(look at the +/- buffers and cache bit). this is normal. it is ubuntu caching information so it runs quicker.

if you actually need this RAM for applications it will be immediately reassigned to such. this isn't a problem and would happen if you just ran ubuntu constantly. nothing to worry about(its actually a good thing, if it wasn't used it would be wasted)

---


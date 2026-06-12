---
title: "Server edition's kernel?"
date: 2009-07-04
forum: Server Platforms
---

### Post by Jestersage on 2009-07-04
I notice that Ubuntu server have a kernel that is specific for server... but what makes it special, in comparison to the generic kernel?

---

### Post by cariboo on 2009-07-04
Have a look at this [page]("http:///www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel"). It explains what is different about the server kernel.

---

### Post by HermanAB on 2009-07-04
Note that the performance difference between the server and desktop versions will not be noticeable in a typical home setup (it won't be noticeable on most servers either, since most servers do very little work).  You can use the desktop Ubuntu to run servers and it will work fine.

The main differences are the server support for more memory and the slower timer tick.

---

### Post by Jestersage on 2009-07-04
Thanks. As some of you probably notice, I am also trying to figure out between RT kernel and Server kernel. While I have yet to find the specs for the RT kernel, I can alsready see the difference.

---

### Post by windependence on 2009-07-05
What are you referring to by RT kernel?

I have seen a big difference on my VMware installs, mostly Zimbra mail servers. For everything else I use *BSD.

-Tim

---

### Post by Jestersage on 2009-07-05
> **windependence said:**
> What are you referring to by RT kernel?


Ubuntu Studio. At the very least, I expect the timing interupt to be different.

Server use 100Hz. Low overhead, high latency. No premption, which allows one task to be performed exceptionally well..
Generic use 250Hz. Standard overhead, standard latency. premption, which is better for multitasking.
RT(Ubuntu Studio) use 1000HZ. High overhead, low latency. 

Basically, ubuntu Studio should be used instead if you have a Core i7 + 6G of RAM.

---

### Post by bigbearomaha on 2009-07-05
RT Kernel is Real Time Kernel.  Used for automation and high spec work in which the kernel MUST depend on highly accurate track of time.

---

### Post by windependence on 2009-07-06
Thanks. I have never heard that reference before.

-Tim

---


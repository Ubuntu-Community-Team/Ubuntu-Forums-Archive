---
title: "n00b needs help with unrecognized lan driver,"
date: 2008-12-26
forum: Server Platforms
---

### Post by lrigoulot on 2008-12-26
I am setting up a server locally and wish to use Ubuntu Server as the OS but
the lan card is not recognised and this leads to problems.  The lan card is an Intel 82575EB and I do not know of any way to install this driver. 

I have no issues with centos 5.2 but I have Ubuntu 8.10 on my laptop and love the support

Any help would certainly be appreciated.

Thanks in advance,
Lou

---

### Post by MaindotC on 2008-12-26
Can you post the output of:
```

lspci
lshw -C network

```

---

### Post by lrigoulot on 2008-12-26
sorry if I did not make myself clear.

I had no lan so after several hours of trying to get Ubuntu to work I installed Centos but missed Ubuntu so much I want to reinstall it but I posted on this forum hoping to get a method of installation.  If this is possible, I will reinstall Ubuntu and follow this thread on my laptop.

The only way to post the return of lspci would be to manually tye it in.

If we can do it I will proceed with the installation.

thanks,
lou

---

### Post by MaindotC on 2008-12-26
> **lrigoulot said:**
> 
The only way to post the return of lspci would be to manually tye it in.


There's nothing wrong with doing that.  Please boot from the Ubuntu Live CD and type that into a terminal and post the output here on the forum.

---

### Post by windependence on 2008-12-26
Also, post the return of:

```
 sudo ifconfig -a

```
-Tim

---

### Post by HermanAB on 2008-12-26
Hmm, if you are new to this and the network card won't work, then it may be a good idea to go and buy another network card.  Those things are a dime a dozen and wasting your time with an obstreperous network card is usually just not worth it.

---

### Post by windependence on 2008-12-26
Herman, I thought he said it was a laptop, but after rereading it your idea is best I think unless the card just isn't coming up for some reason. in that case a simple ifconfig eth0 up would probably do it. There are very few Intel cards that don't work. :)

-Tim

---


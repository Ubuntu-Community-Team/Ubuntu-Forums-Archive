---
title: "Ubuntu server vs ubuntu"
date: 2009-02-14
forum: Server Platforms
---

### Post by balloooza on 2009-02-14
I have already set up my entire server to do what I want it to. But I was allmost sure I installed ubuntu server, not just ubuntu. But it turns Out the wrong disk was used, but it works fine.
Would it be worth it to get the server kernel, or IS that what I would install to make it be "ubuntu server" I am aware all ubuntu is ubuntu and kubuntu is just ubuntu with kubuntu-desktop installed, so is there a meta package to install everything I might be missing (like ubuntu-server) and would hat boost performance.

I need to make sure it will boot into it, because it is a (giant old) headless server, with a wireless card, no ethernet, so the only other option if it didn't boot into server the first time (ie. grub has the server as the default kernel) it would be a pain.

---

### Post by tubezninja on 2009-02-14
The differences between the linux and desktop kernel are outlined here:

[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel)

If these differences are something that you think would affect you, then it might be worth it to install the server kernel.  If not, if you don't know what these things even are, then your install is probably fine as is.


Switching to the server kernel isn't hard.

```
sudo apt-get install linux-server
```

---

### Post by HermanAB on 2009-02-14
You likely won't notice any difference between the different kernels.  The desktop version is slightly more responsive to user input, while the server is slightly more efficient with interrupts.  Nothing worth writing home about though.

Cheers,

Herman

---


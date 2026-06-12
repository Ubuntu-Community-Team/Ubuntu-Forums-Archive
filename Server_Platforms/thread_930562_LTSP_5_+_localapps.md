---
title: "LTSP 5 + localapps"
date: 2008-09-26
forum: Server Platforms
---

### Post by samtay on 2008-09-26
Hey everyone,


Can any one tell me what happing with LTSP 5 and localapps, I just can't seem to find any information on the matter. I have been searching all morning. 

Cheers
Samuel Taylor

---

### Post by samtay on 2008-09-26
Bump

---

### Post by lykwydchykyn on 2008-09-26
I've used LTSP 4.1 in the past, and I'm also trying to get up to speed on LTSP 5.  By localapps, I assume you mean apps installed in the client chroot (hazy on some of the terminology, my LTSP setup was pretty basic).

In LTSP 5 the client chroot is (by default) built using native Ubuntu packages, then compressed into a squashfs image which is shared out by a nbd server (network block device -- I never heard of it before LTSP 5).  

I discovered the best documentation on it is all in the edubuntu handbook.  It has a pretty good explanation of how it works and how to customize things in the client image.

Here's the link:

[http://doc.ubuntu.com/edubuntu/edubuntu/handbook/C/server.html](http://doc.ubuntu.com/edubuntu/edubuntu/handbook/C/server.html)

Hope that helps!

---

### Post by samtay on 2008-09-27
just to update anyone, I was on irc asking about localapps and it should be possible in 8.10.

---


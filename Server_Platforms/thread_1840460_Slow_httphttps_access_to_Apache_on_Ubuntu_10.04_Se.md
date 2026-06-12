---
title: "Slow http/https access to Apache on Ubuntu 10.04 Server"
date: 2011-09-07
forum: Server Platforms
---

### Post by MilesPortent on 2011-09-07
Hi, I've been having a bit of a weird issue for the last few months and I'm really struggling to permanently fix it.

I run a few Wordpress blogs on Apache version 2.2.14 on my Ubuntu 10.04 server box (it's running on an old HP Proliant DL380 G3). I didn't notice any speed issues with accessing the sites 'til switching from a Mac back to a PC, where I started noticing that http requests were very slow, but only when using Google Chrome or Firefox. When using IE, the sites behaved normally at full speed.

After a bit of head-scratching I eventually found out that turning off the TCP autotuninglevel feature on Windows 7 "fixed" the problem when browsing from Chrome and Firefox.

Whilst this works for me, anyone using Windows 7 (and presumably Vista) is going to have the speed issue unless they disable autotuning. I've come to the conclusion that there must be some tweaks on the server that can be performed to improve or negate the problem. 

Has anyone else run into this problem before? If so, perhaps they managed to fix it?

Looking forward to any help or advise, and thanks in advance.

Miles

---

### Post by MilesPortent on 2011-09-08
After some testing last night, the connectivity via SSH and Webmin is also very slow when autotuninglevel is set to normal on Windows 7.

Weird!

---


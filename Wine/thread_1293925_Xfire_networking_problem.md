---
title: "Xfire networking problem"
date: 2009-10-17
forum: Wine
---

### Post by rocky5051 on 2009-10-17
First I'd like to add that I wasn't sure if this was appropriate to start this thread in the wine forum, so if it is better suited elsewhere feel free to move it.

Anyway, I was thinking about running Ubuntu 9.04 on my laptop as the primary operating system as all my needs are met by it (and amazingly every game I want to run on it runs faster through Wine or natively on Linux). The only thing keeping me back is Xfire. Not really because it has problems (which I've found a way to keep it from updating so I can use a compatible, older version), but because at my apartment I'm stuck behind my college's network and xfire cannot connect unless I route it's traffic through a proxy tunnnel.

On Windows I use desproxy to route this traffic through an http proxy. To do that I routed the cs.xfire.com hostname in the HOSTS file to the localhost, then used desproxy to route the traffic through an http proxy. This works, but I'm not entirely sure how to do this on Ubuntu.

I've managed to compile source code for desproxy on linux, and it worked, and the program seems to be working. I just don't know how to set this up.

Any suggestions? Btw, I'm using the 64 bit edition of Ubuntu.

Thanks. :D

EDIT: Now I feel stupid for posting this. I figured it out and got the same setup I have on Windows working on Ubuntu. I just had to figure out where the Linux hosts file was.

---


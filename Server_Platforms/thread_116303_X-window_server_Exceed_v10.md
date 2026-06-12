---
title: "X-window server Exceed v10"
date: 2006-01-12
forum: Server Platforms
---

### Post by jhnaismith on 2006-01-12
Hi there,
  After fooling with Ubuntu on my laptop for a while I upgraded our linux machines computational machines.

We access the linux boxes via a x-windows. Perviously we did this by telnet option in Exceed. 

Ubuntu does not have telnetd and for the obvious reason its insecure we dont want to install it.

I can open a tunnel connect using putty and using Exceed in passive mode, I can simply fire up x-windows.

This is not as easy for my no computer literate colleagues who like the one button click here on icon approach that Exceed offers. We use v10 of Exceed (updated)


I cannot get Exceed to work with secure shell. The problem is either with Exceed configuration or my ssh server configuration. Since I have tried just about every possible variant of Exceed I guess it is something I have wrong on my linux server.

Anyone got advice where to look?

---

### Post by darthyorik on 2007-04-03
You've probably already read this, but just in case you haven't...

[http://the.earth.li/~sgtatham/putty/0.58/htmldoc/Chapter3.html#using-x-forwarding]("http://the.earth.li/~sgtatham/putty/0.58/htmldoc/Chapter3.html#using-x-forwarding")

---


---
title: "Squid!"
date: 2013-03-13
forum: Server Platforms
---

### Post by DanHorniblow on 2013-03-13
Hi, I am very new to squid.

I am trying to setup a content rewirte with squid proxy.

For example, if a web page contained the phrase "Hello world" I would like squid to change it to "Threat detected".

Is this possible?

This is for a Uni project.

Thanks Dan

---

### Post by koenn on 2013-03-13
It's possible - 
I've tried it with apache as a proxy rather than squid when I was debugging a reverse proxy for some misbehaved web applications (and added to my list of interesting techniques for April Fool Projects)

It involves configuring apache as a reverse proxy, and adding an external filter to the configuration  to find and replace phrases/patters in the content that is delivered to the browsers. Apache has built-in support for that  in at least two ways : with a built-in 'sed''module, and a filter filter module that can use any external command, eg sed) 

If you"re  dead set on using squid, I guess it might have similar features, but I wouldn't know what or how.

---

### Post by DanHorniblow on 2013-03-15
I have got it all working now, In the end I ended up using DansGaurdian and Squid.

Thanks for the info though :)

Dan

---


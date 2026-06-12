---
title: "Passing all traffic through one domain to a second server."
date: 2020-08-29
forum: Server Platforms
---

### Post by flagg616 on 2020-08-29
Ubuntu 18.04 Server, Apache
I have three domains that I use and all are hosted on a single, dedicated machine.  One of those domains needs all traffic to be passed on to another dedicated box.  I think it should be simple enough, but I can't seem to find anything relating to it.  Any info would be greatly appreciated.

---

### Post by The Cog on 2020-08-29
I'm not sure what you mean by "domain" 
How about replacing the default route with one that forwards to the desired box?

---

### Post by flagg616 on 2020-08-29
domain1.com, domain2.com, domain3.com.

I want domain2.com to go to a different server box in the same physical location.

---

### Post by flagg616 on 2020-08-29
And yes, a different route to the desired box is exactly what I'm trying to find out how to do.  I assume that I edit the 000-default.conf file but I don't know what syntax to use.

---

### Post by wildmanne39 on 2020-08-29
Moved to the Server Sub-forum.

---

### Post by SeijiSensei on 2020-08-29
Use the reverse proxy feature in Apache.  There are a number of articles about this on the web.  This one is pretty straightforward: [https://www.jamescoyle.net/how-to/116-simple-apache-reverse-proxy-example](https://www.jamescoyle.net/how-to/116-simple-apache-reverse-proxy-example)

---

### Post by flagg616 on 2020-08-29
Thank you.  That is exactly what I was looking for.  I just didn't know what it was called.

---

### Post by SeijiSensei on 2020-08-30
You're welcome. Please go to the Thread Tools drop-down at the top of the page and mark the thread [SOLVED].

---


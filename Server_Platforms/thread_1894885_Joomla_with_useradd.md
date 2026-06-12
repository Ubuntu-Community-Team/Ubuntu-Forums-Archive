---
title: "Joomla with useradd?"
date: 2011-12-13
forum: Server Platforms
---

### Post by djmikepic on 2011-12-13
Hi all,

I'm running Ubuntu 11.10 x86_64 server along with Joomla for web application. 

My site is up and running fine, but I have a question regarding site registrations and Linux user creation (useradd). 

Is there a way to have Joomla also create the Linux user following registration on the site? I have yet to find an extension or plugin which does this....Basically I just need the Joomla to also configure username/password in ubuntu after users register.

Thanks! :D

---

### Post by djmikepic on 2011-12-13
Aplogies, forgot to mention that I'm running Joomla 1.7

---

### Post by Dangertux on 2011-12-13
That's a really bad idea in terms of security. My guess would be a custom PHP script using system exec or passthru...Again this is an absolutely terrible idea.

---


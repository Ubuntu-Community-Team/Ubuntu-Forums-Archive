---
title: "citadel works!"
date: 2008-04-02
forum: Server Platforms
---

### Post by dantheman3212 on 2008-04-02
After a few weeks messing with Citadel, it now works flawlessly. The culprit was Cable One blocking port 25. We got ourselves a static IP and installed and it just worked. I have one last question for you guys regarding this. I'm used to setting up sub domains in a windows server environment, and have not dealt with apache2. I want mail.ptxsolutions.com to go to ptxsolutions.com:8504 or 72.23.13.10:8504, whichever, because thats the port citadel is running off of. How can I go about that?

---

### Post by HermanAB on 2008-04-02
You can use iptables to redirect packets.  Go to Rusty Russel's web site and read a bit.  If you can't figure it out send me a private message and I'll give you an example tonight.  I use these tricks with my own Citadel server.

Cheers,

Herman

---


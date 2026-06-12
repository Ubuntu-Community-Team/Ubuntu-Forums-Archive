---
title: "Problems with modsecurity on ubuntu server 9.10"
date: 2010-04-01
forum: Server Platforms
---

### Post by PatrikJe on 2010-04-01
Hi! 
Didn't really know where to put this thread.

I'm in a big need of help determining the problems caused when I try to install modsecurity. 

I've tried to follow this tutorial: [http://blog.bodhizazen.net/linux/how-to  ... buntu-904/]("http://blog.bodhizazen.net/linux/how-to-mod_security-ubuntu-904/") 
But added the rules from Gotroot instead. 



But the main thing is, when I restarted Apache2 it started complaining that the directory/file /etc/asl/whitelist* couldn't be found that was specified in 00_asl_whitelist.conf 
i changed this to whitelist.txt instead which resulted in that it started to complain about all the domains in domain-blacklist.txt

Has anybody encountered this problem before? 
Can't really put my finger on what the problem might be, or if there's any libs missing...

Thankful for any help i can get.

/Patrik

---


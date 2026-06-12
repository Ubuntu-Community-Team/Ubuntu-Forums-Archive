---
title: "howto configure apache correctly when mythweb seems to be missing it's theme"
date: 2009-09-22
forum: Server Platforms
---

### Post by vipasane on 2009-09-22
Hi!

My mythweb looks currently like this, I'll attach screenshot to this post.

I had a hassle when configuring apache to unstandard port (8081) and securing it. Now changed it back but the appearence is limited to this textbased UI? So what might be the problem?

---

### Post by vipasane on 2009-09-22
Solved: by adding ?RESET_TMPL=true to the URL.
So mythweb was stuck on limited mobile theme. I think it happened when I tested port forwarding with my mobile phone.

---

### Post by Beezleblub on 2009-09-23
Worked for me too ! 
Thanks ! 

And yes, I also tried to login to mythweb using my phone, so seems the rootcause is in mythweb being stuck in mobile mode. 

Cheers !

---


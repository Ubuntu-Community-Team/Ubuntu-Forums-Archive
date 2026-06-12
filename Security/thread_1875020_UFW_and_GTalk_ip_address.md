---
title: "UFW and GTalk ip address"
date: 2011-11-04
forum: Security
---

### Post by Azrael84 on 2011-11-04
Hi,

I've set up the rule ```
 [ 3] 5222,5223/tcp              ALLOW OUT   Anywhere (out) 
``` to enable me to use empathy and GTalk, however I'd ideally like to make these ports available only for connections to talk.google.com, I'm not quite sure of the command for this, I was thinking it might be ```
 sudo ufw insert 1 allow out from talk.google.com to tcp port 5222,5223 
```but it doesn't like the fact it's not an ip address for one.

---


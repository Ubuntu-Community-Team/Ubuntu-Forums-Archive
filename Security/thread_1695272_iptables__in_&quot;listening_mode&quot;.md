---
title: "iptables  in &quot;listening mode&quot;"
date: 2011-02-25
forum: Security
---

### Post by balki2005 on 2011-02-25
Hi,

I would  like  to  setup IPTABLES so  that  the  rules  only  logs  what it will  be do, when they are  activated. 
I would  like to  try  some rules  without to  crash   my  server (blocking wrong  ports, ...  ).

thanks in advance,

Balki2005

---

### Post by The Cog on 2011-02-25
I suppose you could change all the -j DROP lines to -j ACCEPT. Also change the default policies from DROP to ACCEPT. Then you could run it for a while and look at the packet counters to see how much would have been dropped and by which rule.
**iptables -nvL**
will show the counters.

---


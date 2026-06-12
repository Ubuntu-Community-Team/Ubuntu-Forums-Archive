---
title: "Any info about portsentry with iptables"
date: 2010-08-10
forum: Security
---

### Post by methodtwo on 2010-08-10
Hi
I'm not sure if this set up is still used, but i wanted to know how to set up portsentry with iptables so that I.Ps could be blocked if a port scan was attempted from said I.P.I couldn't find any documentation anywhere about this, let alone about this for Ubuntu.If portsentry has been replaced by newer tools please could you tell me what they are and point me to the docs?. Can you achieve blocking dynamically(on demand) with firestarter on it's own?.
It seemed to me when i read about portsentry and iptables(in a book)that this would be an ideal set up.However the book didn't tell you how to achieve this.
Thank you very much for your time
regards

---

### Post by bodhi.zazen on 2010-08-10
I would use psad for that

[http://bodhizazen.net/Tutorials/psad](http://bodhizazen.net/Tutorials/psad)

---

### Post by methodtwo on 2010-08-10
But i don't have to use fwsnort as well right?.That's just for snort/iptables?

---

### Post by bodhi.zazen on 2010-08-10
> **methodtwo said:**
> But i don't have to use fwsnort as well right?.That's just for snort/iptables?

You can use psad with or without fwsnort.

---


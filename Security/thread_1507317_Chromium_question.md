---
title: "Chromium question"
date: 2010-06-11
forum: Security
---

### Post by zypherz on 2010-06-11
Hi there. I'm just trying out chromium browser and I discovered something strange when using it.

I was doing some packet capturing with wireshark when I noticed that Chromium was sending 3 strange DNS queries everytime it starts up. 

1	0.000000	192.168.1.2	4.2.2.2	DNS	Standard query A jlwvwpkoql
2	0.000219	192.168.1.2	4.2.2.2	DNS	Standard query A mlylbpfjfm
3	0.000500	192.168.1.2	4.2.2.2	DNS	Standard query A mrcmyoerab

The A values change everytime it starts up and I was wondering if anyone else has encountered it and could give an explanation on what it could be. Thanks in advance to the gurus and keep up the good work on such a great OS :D

---

### Post by The Cog on 2010-06-11
Very odd. Mine does it, too.

---

### Post by rookcifer on 2010-06-12
You aren't the first one to notice and ask about this.  These DNS queries at start-up are [explained here.]("http://groups.google.com/a/chromium.org/group/chromium-discuss/browse_thread/thread/17bd3e93f3c68448?fwc=1")

Basically it is Chromium's way of stopping ISP redirects to non-existent domains.

---

### Post by zypherz on 2010-06-12
Thanks rockcifer for the link. It helped to explain why Chromium does what it does. At least now I know why :)

---


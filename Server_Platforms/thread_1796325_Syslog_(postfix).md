---
title: "Syslog (postfix)"
date: 2011-07-03
forum: Server Platforms
---

### Post by ricardus1867 on 2011-07-03
Hi!

I've set up postfix on my server. Everything is working great, except that I can't figure out where/if it logs.

From the info I could find on the web, rsyslog should do the logging, but from what I can see, that is not installed as I can't find some files (i.e. /etc/rsyslog.conf) nor any related process when running "ps aux".

I didn't install Ubuntu myself (it's a VPS), so I guess that could explain why it isn't installed (it says everywhere that rsyslog comes with Ubuntu 10.04 by default).

To my question: How do I install rsyslog? Or is there another way to make postfix log?


Thanks in advance

ricardus

---

### Post by ricardus1867 on 2011-07-04
Nevermind.

*apt-get install rsyslog*

was all I had to do.

/facepalm

---


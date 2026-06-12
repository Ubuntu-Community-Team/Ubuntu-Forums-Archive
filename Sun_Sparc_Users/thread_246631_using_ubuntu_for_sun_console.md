---
title: "using ubuntu for sun console"
date: 2006-08-29
forum: Sun Sparc Users
---

### Post by sdstraw on 2006-08-29
Normally I can take one Sun box and connect serial ports with a null modem cable to another since output is echoed to ttya. Then just use tip to display the console on the second Sun system. 

How can I use my Linux X86 ubuntu system to do the same thing? I have COM1 (ttyS0) connected to ttya on the Sun system (Ultra 10). I've tried minicom but the console does not seem to be showing when I run it. Any simple guides on this besides [www.tldp.org?](www.tldp.org?) Or other info?

---

### Post by netztier on 2006-08-29
> **sdstraw said:**
> How can I use my Linux X86 ubuntu system to do the same thing? I have COM1 (ttyS0) connected to ttya on the Sun system (Ultra 10).

For our Ciscos at work I use GTKTerm from the Universe repositories for that. It does not support anything but serial ports. That's about all I want it to do - and _this_ it does sufficiently good.

kind regards

Marc

---

### Post by sdstraw on 2006-09-12
Many thanks, Marc!

Cheers,
Steven

---


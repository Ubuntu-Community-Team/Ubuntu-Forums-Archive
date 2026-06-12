---
title: "Star1 wireless driver - rtl8187b -&gt; rtl8187"
date: 2012-04-06
forum: System76 Support
---

### Post by marshmallow1304 on 2012-04-06
The Star1 wireless driver provided by the System76 driver utility (rtl8187b) stopped working properly with linux-2.6.32-40 on Ubuntu 10.04.  The solution is to blacklist rtl8187b and use rtl8187 as provided by Linux.  The S76 driver should be modified to not install rtl8187b if rtl8187 is available - rtl8187 has supported the rtl8187b chipset since linux-2.6.27.

---

### Post by isantop on 2012-04-06
I'll forward this on to the driver devs, but we haven't had any large support for 10.04 in a while, and with 12.04 coming out in less than a month, I'd doubt it's going to make it in there.

---


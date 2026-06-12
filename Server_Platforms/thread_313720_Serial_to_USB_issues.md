---
title: "Serial to USB issues"
date: 2006-12-06
forum: Server Platforms
---

### Post by mickotoole on 2006-12-06
Hey all,

I'm looking for some help ...

I've attached a Belkin USB Hub to my server and although it says that it's been found when I try to attach a serial to USB cable to either the hub or the server it is not recognised.

Any clue as to what could be the problem?

I've tried installing mod pl2303 and mct_u232 but they don't seem to be helping at all.

Any help would be hugely appreciated.

Regards,

Mick

---

### Post by elst on 2006-12-06
Is this for serial console access? I've connected a server serial console to a laptop running Ubuntu with a null modem cable and a serial-to-USB converter before. In that case, Ubuntu registered the connection as /dev/ttyUSB0 without any extra configuration.

---


---
title: "ltsp 5 local printer"
date: 2007-07-19
forum: Server Platforms
---

### Post by benford on 2007-07-19
I'm trying to configure an ltsp client so that it can access a locally attached (ie to the client) hp deskjet 960c (parallel interface). I'm using Edubuntu 7.04. I found this guide [http://osdir.com/ml/terminal-server.general/2003-09/msg00118.html]("http://osdir.com/ml/terminal-server.general/2003-09/msg00118.html") which seems to only apply to older LTSP setups. 

This guide [http://doc.ubuntu.com/edubuntu/handbook/C/ltsp-client.html]("http://doc.ubuntu.com/edubuntu/handbook/C/ltsp-client.html") seems to be newer. I tried adding the following entry:

```
[MAC Address]
    PRINTER_0_DEVICE=/dev/lp0
```

but it appears to have no effect. Any ideas of what went wrong, or how to diagnose if the printer is being detected at all? Is lp0 even the right device to look for?

---


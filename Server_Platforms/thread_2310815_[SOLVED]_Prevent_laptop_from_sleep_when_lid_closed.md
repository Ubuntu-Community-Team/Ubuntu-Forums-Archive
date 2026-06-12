---
title: "[SOLVED] Prevent laptop from sleep when lid closed"
date: 2016-01-22
forum: Server Platforms
---

### Post by gotcha5832 on 2016-01-22
Dear
I just install ubunut server on an old laptop (samsung 400b2b).
Unfortunately i couldn't avoid sleep when screen are closing form bios?

Do you know I could do it from ubuntu server?

SOLUTION:
edit
[COLOR=#111111][FONT=Ubuntu]/etc/systemd/logind.conf 
add the line:[/FONT][/COLOR]
HandleLidSwitch=ignore

---


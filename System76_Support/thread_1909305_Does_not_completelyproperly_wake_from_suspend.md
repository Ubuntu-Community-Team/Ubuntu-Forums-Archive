---
title: "Does not completely/properly wake from suspend"
date: 2012-01-15
forum: System76 Support
---

### Post by cs35 on 2012-01-15
Ubuntu 11.10
System76 Lemur UltraThin (lem-u2)
i3-330UM Processor  ( 32nm, 3MB L3 Cache, 1.20GHz, 18 Watt)
4 GB - DDR3 800 MHZ 2 DIMMs
Desktop: Unity 3D
Display: Samsung LCD connected via HDMI

Suspend and wake up works fine when I **do not** use external display (Samsung LCD). However on using external display, wake up does not work properly. On wake up I can hear the cpu fan running but display is blank. Mouse pointer is visible and responds to mouse moves. Ctrl+Alt+Del followed by 'Return' logs me out (Though I do not see the logout dialog) - this seems to be the best option though I loose my session. Terminal login which is a result of Ctrl+Alt+F(1-6) does show up (display fine).

Please point me in the right direction in resolving this issue.

Thanks,
cs35

---

### Post by cs35 on 2012-01-16
Found a workaround:

Switching to a console window using Ctrl+Alt+F(1-6) and then switching back to GUI (Ctrl+Alt+F7) displays the Unlock Screen dialog.

---

### Post by isantop on 2012-01-17
I can't replicate that issue on my Lemur here in the shop, so it's not a widespread bug. Can you try running the Lemur from a LiveCD? it could be an issue with your installation. 

Also, ensure that you're going into "Suspend" and not "Hibernate", as the two are very different. Suspend is much stabler and generally much faster.

---


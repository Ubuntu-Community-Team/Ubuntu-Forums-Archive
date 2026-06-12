---
title: "New Ubuntu install.  Who do I get PIA to automatically connect on startup"
date: 2020-01-05
forum: Security
---

### Post by johndill on 2020-01-05
Hi, I would like Ubuntu to automatically connect to my PIA VPN on startup and break any internet connection if PIA is not connected or goes down.  As of now I have to right click on networks, connect to PIA VPN, enter my password every time I start my commuter or take it out of sleep mode.  Any help? thanks

---

### Post by TheFu on 2020-01-06
If you use ifupdown, then you can use the  post-up, pre-down stanzas to handle this.  Unfortunately, I have no idea how to get netplan or any GUI tool how to accomplish the same.

---

### Post by fyfe54 on 2020-01-07
Works for me with no problems.  Check in the settings.

[ATTACH=CONFIG]284762[/ATTACH]

---


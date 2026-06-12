---
title: "Remote Wireless Display"
date: 2021-06-16
forum: Ubuntu, Linux and OS Chat
---

### Post by inquisitive-1 on 2021-06-16
If i were to put Ubuntu on a Raspberry Pi 4 and plug it in to an interactive projector,    Is there any software or feature that would allow windows 10 to remotely connect to it like a wireless display adapter but also return any USB inputs back to the windows 10 device.

---

### Post by cryptik0x756c6f7573 on 2021-07-09
Hey there, i'm a littlebit late i know...  I aint quite informed about wireless display adapters but you could install an OpenSSH server (secure that server) and a VNC server (same goes for that one) on that pi, thus, let you now securely use VNC over SSH on your local network via PuTTY combined with a VNCviewer on your client (windows machine) its not that complicated :)

---


---
title: "VPN Help"
date: 2013-06-26
forum: Server Platforms
---

### Post by motermouth15 on 2013-06-26
I recently installed pptd on my ubuntu headless server (12.04). My goal is to run a VPN server in which I can connect to when I'm not home. I made several successful connections from a computer that is on an external network. A little while later, we tried to re-connect to grab some files and now it gives us error 619. While it's attempting to handshake, the connection shows up as "unknown" in the active connections tab of pptd while viewing on webmin. 

We made no changes to anything on the server in between the successful connections and the unsuccessful connections.

Any ideas why we can't get it to successfully handshake any more?

---

### Post by sandyd on 2013-06-27
Error 619 indicates connection issues with the VPN server itself.

Are there any firewalls in between the VPN Server and the computer you are trying to access it with? If yes, is the VPN allowed, and the ports forwarded appropriately?

---


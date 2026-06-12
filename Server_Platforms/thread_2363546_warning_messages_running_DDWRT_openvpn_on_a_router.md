---
title: "warning messages running DDWRT openvpn on a router"
date: 2017-06-11
forum: Server Platforms
---

### Post by Handssolow on 2017-06-11
I have a router successfully running DDWRT as openvpn client with a commercial VPN provider but there are a couple of issues I'd like to resolve.
First I want to stop the following log warnings -
W WARNING: file '/tmp/password.txt' is group or others accessible
W WARNING: file '/tmp/openvpncl/ta.key' is group or others accessible

adding chmod 600 or sudo chmod 600 or 700 to the DDWRT VPN config breaks the VPN tunnel

most of my searches are contaminated with folk having problems getting a vpn client running on a PC or router.

what do I need to add to my DDWRT openvpn config file to stop these warnings?

---

### Post by wildmanne39 on 2017-06-11
*Thread moved to **Server Platforms**.*

---

### Post by Handssolow on 2017-06-11
My router is running openvpn which is not much different from a PC running as client.
I have different router with openvpn as server, but that's a different story.

My thread is NOT about servers

---

### Post by Handssolow on 2017-06-12
Solved, no warning messages now in the log about this
Router running DDWRT client openvpn, I added in Administration>Commands>Startup
chmod 600  /tmp/password.txt
chmod 600 /tmp/openvpncl/ta.key

---


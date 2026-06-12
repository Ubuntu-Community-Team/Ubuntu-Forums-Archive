---
title: "Need to securely connect Android chat clients to Ubuntu Server 14.04"
date: 2014-07-16
forum: Server Platforms
---

### Post by dave130 on 2014-07-16
I have an Ubuntu 14.04 Server. It runs Prosody (XMPP chat server), and there are 3-10 chat users. All users chat from Android clients.     I'll probably use the incorrect terminology, but **how can I create an encrypted tunnel from the Android clients to my server?**    Other info: the 14.04 server's only purpose is to run Prosody, so I can make any changes to it. The server is home-based and the Android clients use a noip domain to connect to the home server (server runs ddclient to update the IP address).

---

### Post by TheFu on 2014-07-17
I've used a different XMPP server and it had SSL support built-in.  We connected on the default port for XMPPS and all worked.  You'll need to purchase an SSL cert for this. The server documentation should explain it.  You'll probably want a real domainname too.  For something like this server - a micro Amazon EC2 instance (free for first year) is an option. Especially for under 100 clients.

Lacking that feature, **openvpn** is the only other viable solution, IMHO. But I wouldn't want to allow untrusted people onto my home LAN.  The first option really is much better.

---


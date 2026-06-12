---
title: "XMPP via Prosody, but using nginx as SSL terminator?"
date: 2014-08-05
forum: Server Platforms
---

### Post by TheFu on 2014-08-05
I'd like to run prosody for internal company use, but have it available over the internet using SSL. We have an nginx reverse proxy with SSL certs already installed, so I'd like to use those for the XMPPS traffic - talking to the backend XMPP server (prosody) over XMPP (not encrypted on our LAN).

Anyone gotten nginx to terminate non-HTTPS traffic?

Would like for normal XMPP clients to just use XMPPS for the connection.

I'm I crazy?

---


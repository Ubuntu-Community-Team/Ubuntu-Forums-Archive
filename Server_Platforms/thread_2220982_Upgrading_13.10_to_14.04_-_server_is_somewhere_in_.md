---
title: "Upgrading 13.10 to 14.04 - server is somewhere in limbo"
date: 2014-04-30
forum: Server Platforms
---

### Post by m3rtijn on 2014-04-30
I don't have physical access to the server atm, but this is what happened.
I did a `do-release-upgrade`as I did with previous upgrades. All joy. Seems to be working absolutely fine. Then I went afk, came back only to see it's asking a question. I answer with the default by hitting Enter.

Then it happened.

Connection closed.

Reset session -> nothing. SSH is not responding. I let it sit for a few minutes, but still no joy.

This is the second time I've come across this, so it's not an edge-case anymore. It seems like the server is rebooting but is being stuck somewhere. But because I don't have physical access atm, and SSH isn't up (yet), I have no idea what's trying to do that doesn't work.

But seriously, why ask a question and then close the connection? What's the advantage of doing that??

---


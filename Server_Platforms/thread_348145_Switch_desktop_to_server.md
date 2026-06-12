---
title: "Switch desktop to server"
date: 2007-01-28
forum: Server Platforms
---

### Post by ethrandil on 2007-01-28
Hi,
I'm running Ubuntu Dapper on my backup server. Is there a Way to get rid of those desktop packages and switch to the server version belatedly?

mfg
- eth

---

### Post by igknighted on 2007-01-28
Yes, but it might be more work than downloading 'server' and reinstalling.  You would apt-get remove all programs that you no longer want, then apt-get install the server packages you need.  There of course would be no harm leaving the desktop packages there (a gui makes for easier maintenance) but I would stop all the desktop specific services from loading at boot.

---


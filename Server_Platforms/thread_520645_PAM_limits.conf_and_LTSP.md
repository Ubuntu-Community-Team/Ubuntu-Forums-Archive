---
title: "PAM limits.conf and LTSP"
date: 2007-08-08
forum: Server Platforms
---

### Post by flygin on 2007-08-08
I tried to limit the number of open applications of LTS users with PAM limits.conf. It works for a few minutes, then nobody can log in anymore.
the LTS server is in a classroom with 60(!!) stations and the kids are between 9 and 13 (!!!). In a testrun they crashed the server within 10 minutes.

We want to force them NOT to use more than 5 progs simultanously.

Any suggestions for PAM limits.conf?

any other way (pkill with cron???)

---


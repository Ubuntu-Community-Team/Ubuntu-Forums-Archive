---
title: "Running one copy of postgrey and making it available to multiple instances of postfix"
date: 2015-05-24
forum: Server Platforms
---

### Post by doktor-kill-patient on 2015-05-24
Hi,

I've got a few ubuntu LTS servers running postfix in different parts of the world. I've recently implemented postgrey greylisting because it is incredibly effective in stopping SPAM. The greylisting period is a relatively short 300 seconds.

The problem I'm experiencing when an email is sent by a remote host, the first mail relay server greylists it. Then the remote host thinks there is something wrong with this server and tries the second one. Then the second one greylists it.. and so on and so forth. This can delay e-mail for a very long time (30+ minutes).

So is it possible to 'share' the postgrey database between all the mail relay servers?

If yes, what is the most elegant way to accomplish this?

---


---
title: "how to report a recurring bug?"
date: 2012-04-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Baldrick_NZ on 2012-04-02
Hi all,

I have a bug where sometimes the login screen has several attempts at landing on screen. It does eventually. Only then can I actually login.

My question is, how can I report a bug that happens before I'm actually logged in? Is there a log that would take into account these login attempts, which I could access in order to report? 

I get errors that apport picks up after logging in, how would I know whether they are connected with the login attempts?

Any help would be much appreciated!

---

### Post by mc4man on 2012-04-02
There are various logs in /var/log/lightdm, maybe something in one or more of them that's relevant/useful

---


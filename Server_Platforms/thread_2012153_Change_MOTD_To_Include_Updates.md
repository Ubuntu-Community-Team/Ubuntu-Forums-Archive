---
title: "Change MOTD To Include Updates"
date: 2012-06-28
forum: Server Platforms
---

### Post by bsntech on 2012-06-28
Hello all,

Hopefully this is a fairly quick question/answer.

Upgraded from Ubuntu 10.04 to 12.04 Server.

I noticed if you install 12.04 by itself, you see some information upon logging in to an ssh session about what updates are available.

However, when upgrading from 10.04 to 12.04, this doesn't show up.

I tried to install the update-motd package - thinking this would do it, but no success.

Thank you!

---

### Post by CharlesA on 2012-06-28
You need the update-notifier-common package installed.

---


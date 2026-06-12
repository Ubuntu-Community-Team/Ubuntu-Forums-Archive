---
title: "Sendmail uninstall ..."
date: 2005-11-09
forum: Server Platforms
---

### Post by dbee on 2005-11-09
Why  does the sendmail uninstall remove my mysql server ??

---

### Post by heimo on 2005-11-09
Because MySQL server depends on mailx, which depends on MTA - like postfix, or any other mail transfer agent:
[http://packages.ubuntu.com/breezy/virtual/mail-transport-agent](http://packages.ubuntu.com/breezy/virtual/mail-transport-agent)

---


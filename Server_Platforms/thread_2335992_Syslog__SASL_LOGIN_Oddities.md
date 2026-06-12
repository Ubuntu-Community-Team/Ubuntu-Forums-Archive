---
title: "Syslog / SASL LOGIN Oddities"
date: 2016-09-03
forum: Server Platforms
---

### Post by netiquity on 2016-09-03
Hi,
I have a rather odd situation, or at least it is to me.
I have two identical servers running Virtualmin on Ubuntu 16.04.
I have been looking through the logs to further investigate a lot of failed SMTP logins, and on one server I notice the line says:
Sep 3 12:01:59 triton postfix/smtpd[17303]: warning: [REMOVED]: SASL LOGIN authentication failed: authentication failure
and on the other it is:
Sep 3 11:52:04 hydra postfix/smtpd[13264]: warning: [REMOVED]: SASL Login authentication failed: authentication failure
Whilst only a minor difference LOGIN/Login this does seem odd and causes issues when using grep to search logs.
Does anyone have any suggestion on how this might of happened, or what can be done to make the two match.
Thanks

---

### Post by Habitual on 2016-09-06
postfix **versions**?

---


---
title: "LTSP session open/close in endless loop in auth.log"
date: 2010-05-26
forum: Server Platforms
---

### Post by kfleten on 2010-05-26
I have a LTSP session who goes on opening and closing on my system. In auth.log I have this message:

CRON[27948]: pam_unix(cron:session): session opened for user tobias by (uid=0)
CRON[27948]: pam_unix(cron:session): session closed for user tobias

The message goes on in a endless loop with a duty cycle of one minute. How can I solve this ?

---


---
title: "initctl error while making script for M/Monit"
date: 2013-04-07
forum: Server Platforms
---

### Post by HL521 on 2013-04-07
Hey guys, I am receiving this error:

```
initctl: Rejected send message, 1 matched rules; type="method_call", sender=":1.9" (uid=1000 pid=2379 comm="initctl reload-configuration ") interface="com.ubuntu.Upstart0_6" member="ReloadConfiguration" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")
```

from [http://mmonit.com/wiki/MMonit/Setup](http://mmonit.com/wiki/MMonit/Setup)

Not entirely sure how to procede. Many thanks!

---

### Post by chrisguk on 2013-04-07
I believe your answer will be contained here:

[http://askubuntu.com/questions/153064/user-upstart-job-in-init-is-not-found](http://askubuntu.com/questions/153064/user-upstart-job-in-init-is-not-found)

---

### Post by HL521 on 2013-04-07
> **chrisguk said:**
> I believe your answer will be contained here:

[http://askubuntu.com/questions/153064/user-upstart-job-in-init-is-not-found](http://askubuntu.com/questions/153064/user-upstart-job-in-init-is-not-found)

Thank you for the reply.

However, I was curious- how would the user config [~/.init/] affect the global? Because I thought this is what

> from [http://mmonit.com/wiki/MMonit/Setup](http://mmonit.com/wiki/MMonit/Setup)

was trying to do in the first place.

---


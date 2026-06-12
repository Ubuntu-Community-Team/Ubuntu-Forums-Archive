---
title: "fail2ban log rotation"
date: 2010-09-14
forum: Server Platforms
---

### Post by stlsaint on 2010-09-14
hey folks i have been doing some digging but i have come up with non-working solutions. So i have fail2ban on server but everytime fail2ban conducts a log rotation it unbans all the banned IP's. I have ip's to be banned for a week whenever a log rotation happens or i restart fail2ban i dont want all the ip's released! I was thinking there was a script or patch that would fix this but i have come up short. Any ideas?

---

### Post by stlsaint on 2010-09-15
UPDATE: Seems this was a bug in previous releases. Mine is updated with the newest release but still having the same issue!

---

### Post by mistypotato on 2010-10-16
Just ran into this myslf.

I had bans set to one month.

All bans were dropped when I rotated the logs.

Now all the bad guys get  a fresh shot to break in :confused:

---


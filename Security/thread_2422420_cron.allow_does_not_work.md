---
title: "cron.allow does not work"
date: 2019-07-07
forum: Security
---

### Post by marty23a on 2019-07-07
Hi,

during the hardening process for Ubuntu 18.04 LTS I used/created the cron.allow file at /etc/. I only added "root" in the first line. Afterwards I logged out and logged in as user. I am still able to use the "crontab -e" command. I also did the opposite and added the user to the created file "cron.deny" (after I deleted the cron.allow). I am still able to call the command crontab -e as user.

I was not able to any entry that describes the same issue in order to find a solution.

Does anyone has an idea ?

BR

---


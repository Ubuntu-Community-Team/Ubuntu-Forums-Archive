---
title: "Missing /etc/cron.daily/apt"
date: 2012-01-09
forum: Server Platforms
---

### Post by linex83 on 2012-01-09
I setup the unattended-updates package on my ubuntu 11.04 server. However, I soon found that it is never executed, since no log files are created. I tried to run it manually. I could see the created log files, so running is not a problem. My research led me to the missing /etc/cron.daily/apt. All manuals I found online just assume that the file exists, e.g. this one: [https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)

Apparently this file does not exist on my system. Using apt-file I found that it should be part of the apt package. Which is, of course, installed. I tried to run dpkg-reconfigure and see if it is created - but it is not...

My conclusion is that the file should be there, but it is not. Do you have any ideas what the problem might be?

---

### Post by Paqman on 2012-01-15
I've just struck the same problem on a new VPS. I'm thinking the owners might have trimmed it out of the cron setup?

---


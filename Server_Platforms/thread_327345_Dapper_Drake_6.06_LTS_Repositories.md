---
title: "Dapper Drake 6.06 LTS Repositories"
date: 2006-12-29
forum: Server Platforms
---

### Post by cmccrea on 2006-12-29
Relative Newbie to linux, and have dived straight in attempting to configure a test ubuntu server at home. Have enabled the root account and have managed to install the ssh terminal as per the instructions at [www.howtoforge.com](www.howtoforge.com).
I am located within Australia and my repositories list is configured to access the au sites. At the moment it simply reports that it is unable to fetch any updates, security included.

Are there dedicated repositories I can put in the list that are sure to work. Want to check that it isn't anything on my machine

---

### Post by mats.lundqvist on 2006-12-29
have you tried just accessing the internet with a browser or using ping?

---

### Post by Brazen on 2006-12-29
> **mats.lundqvist said:**
> have you tried just accessing the internet with a browser or using ping?

Ditto, try pinging (from the server) [www.google.com](www.google.com).  If that works, try pinging the repos.  One thing I've done, is after setting a static IP, I always forget to set the gateway.  Extensive pinging will help determine if your problem is apt-related or network-related.

---


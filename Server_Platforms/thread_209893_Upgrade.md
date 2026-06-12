---
title: "Upgrade"
date: 2006-07-05
forum: Server Platforms
---

### Post by jordans on 2006-07-05
I am just full of questions today, hope that  isn't bugging anyone. My question is: Is it possible to upgrade to 6.06 from 5.10 without reinstalling it. I am running an webserver and it would be a pain to have to reinstall everything. This may be a really stupid question so someone tell me if it is. 
Thanks

---

### Post by Randomskk on 2006-07-05
It is, although it may not work nicely.
Back up everything first, then open the file /etc/apt/sources.list as root, and change every mention of "breezy" to "dapper", save, and do these two commands:
sudo apt-get update
sudo apt-get dist-upgrade

Then you'll be running Dapper, although it may not work nicely in which case you'll need to manually resolve the issues.

You may just want to stick with Breezy for the time being.

---


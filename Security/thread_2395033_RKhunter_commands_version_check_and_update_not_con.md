---
title: "RKhunter commands version check and update not connecting (solved)"
date: 2018-06-25
forum: Security
---

### Post by oceola2 on 2018-06-25
When rkhunter 1.4.6 is installed, if you've never set the WEB_CMD command look in the rkhunter.conf file.
I've been using rkhunter since Hoary Hedgehog and never had an issue like this.
Usually this is set to a default null string ' ' and it functions  properly for the update and version check in all those versions of  Ubuntu before the Beav.
Instead of the default null string the repository version has /bin/false instead of the null string.
Took me a while to figure out why the versioncheck and update weren't working.
Set it to a null string if you have an issue or write in wget or curl, it should default with the null string IMO.
Also the versioncheck will go to a Canonical address and show the proper  version and the update will go to the proper RKhunter servers for your  language or all of them.

---


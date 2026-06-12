---
title: "System not checking for updates"
date: 2013-04-16
forum: Ubuntu Development Version
---

### Post by wgarcia on 2013-04-16
I have a system where I have the development version 13.04 that is not checking for updates. In "System Settings" I have "check daily" marked, and also "Display immediately" in both appropriate places. 

From the command line "sudo apt-get update" completes without any error, and "sudo-apt-get upgrade" afterwards installs all the available updates without error. The system refuses to tell me about updates, if I don't issue the "update" command manually no updates are offered.

I'm behind a proxy that is working perfectly otherwise. I have checked /etc/environment and /etc/apt/apt.conf and I can see the proxy correctly defined in these two places, and in any case as I said "sudo apt-get update" and "upgrade" from the command line finds the repositories that I use without any error. Once I issue "update" from the command line, I get the indicator that there are updates (I have it configured to show it to me in the upper panel and this is what the system does once I "update" manually). 

What can be preventing my system to check updates automatically?

I also have some other systems already upgraded to 13.04 and they are reporting updates as usual, it is just in this system that this is happening.

---


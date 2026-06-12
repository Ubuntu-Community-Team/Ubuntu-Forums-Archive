---
title: "disable firestarter messages"
date: 2009-10-31
forum: Security
---

### Post by tnvkrishna on 2009-10-31
Hi all,
I have recently installed firestarter (frontend to iptables).
and added it to list of sudoers and in startup programs .
the system tray does showup at startup but since almost allways
my ethernet cable is not connected or my wireless connection is
not enabled before startup .. I get this message
"the device eth0 is not connected"
or
"the device wlan0 is not connected"

I just want to disable this popup at startup even though
my connection is not enabled .. any suggestions

And do you suggest any other more sophisticated fronted to iptables

thanks in advance

---

### Post by QLee on 2009-10-31
The simple answer if you don't want to see those messages is to not run the GUI at startup. It is a front end for configuration but it doesn't have to be running for you to be protected by iptables, installing it has already written the default rules to iptables. You might get tired of it showing you all the hits it's blocked and it uses resources, so no need to keep it running unless you're using it for something, like monitoring your connections or hits.

Lots of people here don't like firestarter and will recommend another frontend. I'm not sure why you need "sophistication" for a frontend to iptables.

---


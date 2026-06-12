---
title: "My proxy server just gets more interesting"
date: 2009-12-03
forum: Server Platforms
---

### Post by werner.fletcher on 2009-12-03
Hey guys,
 
I've got a DHCP Squid proxy server running in a hotel environment.  What's been asked of me now is that guest internet usage be monitored.  This where it gets interesting.... See, squid is blocking certain sites like youtube, facebook etc.  Now they want me to do it so that ppl are blocked by default, but if they want to view the blocked sites they will be monitored and charged accordingly.
 
Any ideas??  Thanks in advance!  :)

---

### Post by riste on 2009-12-04
I know someone who's modified DansGuardian and squid to do website logging and added a PHP portal to configure it and view the logs.  You might try a similar setup if you are, or have use of, a web developer.  You'd have to figure out how to authenticate individual guests, and also how to get the usage data sent to the billing system.  It would be a few levels of complexity up from what you have now, so it may not be worth the effort depending on how much usage it would get.

---

### Post by slakkie on 2009-12-05
Monitoring customers? Are they sane?

---


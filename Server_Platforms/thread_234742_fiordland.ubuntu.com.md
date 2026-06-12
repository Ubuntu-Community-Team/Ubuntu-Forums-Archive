---
title: "fiordland.ubuntu.com"
date: 2006-08-11
forum: Server Platforms
---

### Post by waveslider on 2006-08-11
What is this?? This showed up as an incoming connection that was blocked by Firestarter. Why is someone from fiordland.ubuntu.com attempting to connect to my PC?

[IMG]http://tom.g27.org/images/Screenshot.png[/IMG]

---

### Post by morgs on 2006-08-14
ntp.ubuntu.com resolves to the same IP address as fiordland.ubuntu.com so I think this is the reply to an ntp query.

HTH,
Morgs

---

### Post by misterfixit on 2007-09-14
This is your ubuntu box connecting to the Time Server.  NTP is "Network Time Protocol".  Most likely your box is set up so as to do a correct time of day check every so often.  Most users can set the interval to every 30 days unless you are doing second-count critical work and then you can set the NTP interval to every 24 hours.  That reduces congestion on the various time servers.  How the time servers work, you can Google for "Network Time Server" and find out more than you will ever want to know about time, the lack thereof, the counting of, the making of, the history of, the future of, the Time Lords and the average time it takes for a female to achieve orgasm.

HTH,

Dave

---


---
title: "DNS named resource utilization"
date: 2008-01-07
forum: Server Platforms
---

### Post by dachinster on 2008-01-07
Hi,
I know this is a Ubuntu forum, but right now I have a Redhat 8 DNS server that shows steadily increasing memory utilization for the 'named' process.

I restarted the service as well as stopped and then started the service and it dropped from 85% to 2% but it has slowly increased over the hours and is now up to 45% and increasing.

I have over 6000 people utilizing the DNS service, and management is becoming difficult.

In the interim, I am going to set up a cron job to restart the service every 4 hours or so, but this will cause interruptions.

Is there any way to avoid this and any assistance that you guys can provide me with please?

---

### Post by MJN on 2008-01-08
You haven't said what version you're running (hence it could be a now-fixed memory leak in an old version) however are you using max-cache-size to clear out older entries that haven't hit their TTL when the limit is reached?
 
You ought to post this in a RH forum as we could be chasing our tails looking for a problem that may well be RH-specific.
 
Mathew

---


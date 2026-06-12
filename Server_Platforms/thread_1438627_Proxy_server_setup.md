---
title: "Proxy server setup"
date: 2010-03-25
forum: Server Platforms
---

### Post by hansonian on 2010-03-25
I'm using a extra machine I had laying around as a proxy server for some windows machines. I'm running TinyProxy, Dansguardian and Firehol on it to limit what websites are available for viewing on the windows machines. This all works fine but I have a need to "stop" the url filtering for a short time every day and this is where my problems arise. My plan was to run a cron job to stop and start Dansguardian at certain times so my windows machines would have unfiltered access, sounds good in theory. When I stop Dansguardian it blocks all urls, even the ones I have on my exception lists. I'm thinking I have something to do with the proxy misconfigured but for the life of me I can't figure it out. If anyone has any suggestions I would greatly appreciate it.

thanks

---


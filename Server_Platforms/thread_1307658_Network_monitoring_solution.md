---
title: "Network monitoring solution"
date: 2009-10-31
forum: Server Platforms
---

### Post by DCK on 2009-10-31
I have a personal server running on my campus flat. The campus ISP allows me to download and upload whatever I want around campus, but when it comes to connections off campus (a certain IP range), I can only upload a certain amount of data per week. Because I have people using services on my server outside the campus, there's a real possibility that I may cross this limit.

To prevent that from happening, I need a tool that allows me to monitor the traffic I send to locations in the IP range that's not the campus, so I can check whether I need to stop offering those services. It should also be possible to refresh it easily weekly (probably a cron job).

The IP traffic tools that I tried (IPTraf, bwm-ng) are focussed more on monitoring network load (they measure bandwidth, and I don' rather than finding total network usages, and don't seem to provide any means to differentiate between IP ranges.

Does anybody know a tool that I can use to help me comply to my ISP terms of use :)

---


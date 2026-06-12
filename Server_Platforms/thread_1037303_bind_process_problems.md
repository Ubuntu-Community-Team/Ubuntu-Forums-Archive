---
title: "bind process problems"
date: 2009-01-11
forum: Server Platforms
---

### Post by ezacon on 2009-01-11
I have a home server (8.04) as gateway and firewall.
I have a strange problem with bind.
From time to time, bind stops forwarding requests to external name servers. It still resolve requests for wich it is authoritative.
At this moment, if i try to restart bind, the process is unable to stop bind. I need to kill bind process and start it again and it works fine again for some time. i have not see any message in syslog related to bind.
Any idea how to start debuging this ussue?

Thanks

---


---
title: "Router failover to internal web server"
date: 2012-02-09
forum: Ubuntu Dev Link Forum
---

### Post by ChrisEdgington on 2012-02-09
I've got an idea for a router customization. I've got a router that is based on Ubuntu. I want to write something or configure an existing component so that when the WAN connection goes down, further requests for web browsing server up a page from the internal web server. So, for example, say I'm browsing the web from my iPad through this wireless router. The connection attached to the WAN port is lost. Now instead of the iPad browser displaying a "page not found" or something like that - it displays a nicely formatted page that says "WAN connection lost. Reboot modem." - or something like that. My questions are this:

1.
How would I detect that the WAN connection is lost? Would I need to have a process like keepalived or something similar running that I could query to see if the network was still up?

2.
How would the switchover from passing port 80 requests on through to the WAN to just serving up from the internal web server get accomplished?

Thanks for any ideas.

-Chris

---


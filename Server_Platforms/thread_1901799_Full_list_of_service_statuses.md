---
title: "Full list of service statuses"
date: 2011-12-29
forum: Server Platforms
---

### Post by kevpatts on 2011-12-29
Hey guys,

Can someone tell me how to get a full list of services and their statuses? I know most run under SystemV and some are Upstart, but is there a script or a command that I can run to simply show that status of all services?

"services --status-all" is terrible (and SystemV only) but if you run:```
sudo sed -i "s@\\\Wstatus)@\\\W*status)@" `which service`
``` it gets a little better. "initctl list" only does Upstart ones.

I really thought Ubuntu would have moved all scripts over to upstart by now seeing as they've been using it for years!

Kevin

---


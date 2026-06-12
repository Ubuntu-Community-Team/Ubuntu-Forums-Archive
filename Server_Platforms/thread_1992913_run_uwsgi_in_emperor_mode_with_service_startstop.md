---
title: "run uwsgi in emperor mode with service start/stop"
date: 2012-06-01
forum: Server Platforms
---

### Post by l0rd on 2012-06-01
Hello!
I use Ubuntu 12.04. My uwsgi version is 1.0.3.
I put my vassals config files in /etc/uwsgi/apps-available, also create links in apps-enabled.
When I do service uwsgi start, nothing happens. Where are no entries in logs.
But when I do uwsgi --emperor /etc/uwsgi/apps-available, it's Ok, my applications starts normally.
So, how to start uwsgi in emperor mode with service start/stop?

---


---
title: "dpkg not cleaning"
date: 2012-04-20
forum: Server Platforms
---

### Post by jr_ on 2012-04-20
I had munin installed and uninstalled it a few days back. Yet the cronjobs for this package continue to run. I used aptitude remove then dpkg -P. The man page explains that -P "removes everything  except  conffiles."

I can understand leaving log files around but it seems dpkg considers cron files to be conffiles. Is there a switch in dpkg I'm missing that would completely remove all traces of the software? or is this functionality included in another package?

Why does dpkg not remove files which are being executed after the exit of the software?

---


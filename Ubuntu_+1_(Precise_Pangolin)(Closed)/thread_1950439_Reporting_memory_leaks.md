---
title: "Reporting memory leaks?"
date: 2012-03-31
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kyleabaker on 2012-03-31
As Ubuntu 12.04 matures, I'm noticing that slow creeping memory leaks are not under control and would like to help by generating/collecting useful data for bug reports.

For example, I notice that just after boot-up the unity-panel-service steadies off around 10-12 MiB. After 2-3 hours of use its now consuming 87 MiB. There are many other process that do this as well. I'd like to find out how I can collect useful information to attach to a bug report.

I've looked into valgrind a little, but if someone could provide an example (for instance with unity-panel-service which starts up by default) I would appreciate it! Thanks!

---


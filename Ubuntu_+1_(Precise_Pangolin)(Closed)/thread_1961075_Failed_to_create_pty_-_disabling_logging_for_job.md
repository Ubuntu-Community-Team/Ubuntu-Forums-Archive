---
title: "Failed to create pty - disabling logging for job"
date: 2012-04-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by TimHeckman on 2012-04-18
I opened a bug on Launchpad, and haven't heard anything about this so I thought I'd poke around here:

- [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/980917](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/980917)

I'm working on using Ubuntu 12.04 as a domU under Xen.  When booting up I get a large number of errors on my hvc0 console, these two repeating:

====
init: Failed to create pty - disabling logging for job
init: Temporary process spawn error: No such file or directory
====

Any ideas on what the cause may be?  The issue doesn't happen on a VirtualBox instance, for example.

-Tim

---


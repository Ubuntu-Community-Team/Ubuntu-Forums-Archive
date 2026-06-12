---
title: "Multiple machines in a cluster?"
date: 2018-12-06
forum: Server Platforms
---

### Post by psychodelic2 on 2018-12-06
Hi!

I have a specific question about my servers. At this moment I have 1 server for the application (working on elixir / erlang) and one for the database (cassandra) - both Ubuntu 18.04.
I would like to upgrade to two and more servers, just to ensure redundancy and HW load balance.

What is the best approach to achieve redundancy (if one server goes down, nothing really happen) and proper load balance (if one server reach out of memory it will not be used)?
Use some cluster like Kubernetes or what do you suggest?

Thank you in advance!

---


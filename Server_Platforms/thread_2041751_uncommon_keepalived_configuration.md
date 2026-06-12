---
title: "uncommon keepalived configuration"
date: 2012-08-13
forum: Server Platforms
---

### Post by hl2x on 2012-08-13
Hello everyone,

since an expert told me that my configuration of keepalived is uncommon (but not wrong), I would appreciate your opinion and expertise. Especially, I would like to know whether I can run into complex or undefined situations, for example race conditions. So here is the configuration:

[LIST]
[*]4 virtual machines on two hosts, which are all able to act as router to a new network segment
[*]One vrrp_instance, grouping inside and outside, so any of the 4 machines can get master router
[*]In addition, the 2 machines belonging to the respective phyical host are routers to a small protected dmz within the host. For this, these 2 machines form another vrrp_instance (using different router ips, ids and passwords).
[*]As a result, every configuration has two vrrp_sync_groups and four vrrp_instances.
[/LIST]
The behaviour of this configuration seems fine. The routing function in the new network can be realized by all 4 systems, while the routing to the dmzs can be performed by the 2 systems belonging to the respective physical host.


What do you think about the config?

---


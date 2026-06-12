---
title: "Does UEC Make Sense For this situtuation"
date: 2012-04-18
forum: Ubuntu Cloud and Juju
---

### Post by kkcv on 2012-04-18
We are a small business looking for a good solution for HA and DR. Currently we are running a vmware/veeam cluster using local storage to handle internal dr issues. We are looking for a good cost effective solution to move this so that we have an external soltuion. 
 
In the past I have used centos and DRBD to cluster storage and been able to effectivly down one server and using Heartbeast easily bring up VM's on a passive cluster.
 
What I want to know is this. If we use mutliple ubuntu cloud servers clustered using internal storage do the VM's replicate much like I could with drbd and heartbeat? Secondly if I want to replicate these VM's to amazon ec2, do they real time replicate or is this scheduled? 
 
I realize this is not a traditional use of cloud, that the idea is more how we can quickly spin up machines but I believe this might be one good usage for a small business.

---


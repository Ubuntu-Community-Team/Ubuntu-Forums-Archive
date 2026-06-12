---
title: "Better configuration for deploying virtual servers and machines"
date: 2020-01-14
forum: Ubuntu Cloud and Juju
---

### Post by coyotekojo on 2020-01-14
Hello everyone, i am looking for some advice before taking any decisions, i have 5 old Hp proliant servers (from gen5 to gen8) that were purchased when needed every time we started a new company or had a new project, as per today i am only using 2 of the servers, one for my company accounting software and the other for a crypto currency pool, everything is working just fine and i am not sure if i want to make it more complex, but since i have many servers i was thinking to setup a cluster, and run virtual machines on it for the plus of having HA in the case one of the servers goes down, the pool is running on Ubuntu 18 and have no questions here, my company software only runs on windows server so having a windows server running on a virtual Ubuntu server is a good idea? is deploying an HA Ubuntu cluster to have redundancy on my virtual machines a good idea? i was thinking that getting all servers together will be the best way to go for me as i already have most of the hardware, does anyone see a problem with my idea? thank you

---

### Post by TheFu on 2020-01-15
It depends.

The answer depends on your needs, requirements and desires.  Proliant gen5 HW has had compatibility issues with Linux previously so I wouldn't assume it to be compatible. Previous certified HW lists are for specific versions of Ubuntu. That doesn't mean any hardware will be compatible for all later releases.

---


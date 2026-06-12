---
title: "Accessing machines deployed by Autopilot"
date: 2017-04-18
forum: Ubuntu Cloud and Juju
---

### Post by mohamad17 on 2017-04-18
I am trying to deploy an Openstack cloud on a cluster of machines using Autopilot, as shown in [https://www.ubuntu.com/download/cloud/autopilot](https://www.ubuntu.com/download/cloud/autopilot). I can get through all of the steps successfully, however, all of the machines, commissioned by my MaaS, and then used for the Openstack deployment are not reachable via ssh. I have my ssh keys configured in MaaS, and if I deploy a machine manually, I can ssh into it. It is the machines that are deployed through autopilot that are no longer accessible. Is there any non-intrusive way to access the machines remotely? I hate to stop the machines and boot them into rescue mode since they are used as part of the cloud.

---


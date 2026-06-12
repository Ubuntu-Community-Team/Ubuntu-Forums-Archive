---
title: "platform"
date: 2011-09-09
forum: Ubuntu Cloud and Juju
---

### Post by reema on 2011-09-09
Hello..

I want to ask about the platform ..how we can develop our own application and which platform we can use it to deploy it on UEC ?

---

### Post by kim0 on 2011-09-10
Hi,
If you're interested in writing applications on top of any cloud solution, I'd encourage you to check out Ensemble
[https://ensemble.ubuntu.com/](https://ensemble.ubuntu.com/)

It's a deployment and orchestration tool that can work on top of ec2, openstack (next ubuntu cloud) or even a local machine (coming soon). The basic idea is that you deploy some services (mysql, caching, ...etc) and write apps that make use of it

---


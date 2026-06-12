---
title: "suspend resume migrate bug? in XEN 4"
date: 2011-11-28
forum: Server Platforms
---

### Post by hackoon on 2011-11-28
ubuntu 11.10 has problems running XEN 

suspend/resume, migrate or Dom0 reboot leaves vif -interfaces broken

it does happen 1 in 2 trys  normally DomU still receives data but is unable to send anything after DomU-resume

system is ubuntu 11.10 on DomU/Dom0 with 3.0.13 kernel basic installation without GUI or anything
log isn't showing anything unusual 

temporally workaround is to detach and attach the interfaces manually but its not a reliable solution for our propose. If we can' t solve this problem we have to deploy a different distribution.

hackoon

---


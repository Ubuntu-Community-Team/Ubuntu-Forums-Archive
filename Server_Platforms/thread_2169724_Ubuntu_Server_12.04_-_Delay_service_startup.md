---
title: "Ubuntu Server 12.04 - Delay service startup"
date: 2013-08-23
forum: Server Platforms
---

### Post by Gantlett on 2013-08-23
Hello,

My Ubuntu server is running CrashPlan which backs up some SMB shares. The shares are mounted to folders using fstab.

The problem is that when the server starts up, CrashPlan sometimes sees the folders as empty. When I run *sudo mount* I can see the shares are mounted and I can also access them just fine. Restarting the CrashPlan service brings it back to its senses.

I assume the service starts up quicker than the shares are mounted. Is there a way to delay the startup of a service?

Thanks

---

### Post by chrisguk on 2013-08-23
I believe you are talking about re-ordering services within upstart.  Have a look at this guide and see if it gives a suitable resolution.

[http://upstart.ubuntu.com/cookbook/#guaranteed-ordering-of-services](http://upstart.ubuntu.com/cookbook/#guaranteed-ordering-of-services)

---

### Post by Gantlett on 2013-09-15
Thanks for your response and apologies for the late reply - I wasn't notified of your post...

I have read about this and found that the update-rc.d utility can achieve what you are suggesting. However I'm quite hesitant to use it as I'm not sure even what the current values of the service are and what my boundaries are or if my settings would conflict with another service/s... Is there a way to get a better idea of what values may be appropriate? Is there anything safe I can try?

---


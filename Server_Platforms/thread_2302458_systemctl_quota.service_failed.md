---
title: "systemctl quota.service failed"
date: 2015-11-10
forum: Server Platforms
---

### Post by rhandy2 on 2015-11-10
How to fix it???

> Nov 10 18:29:25 example.com systemd[1]: Starting Check And Enable File System Quotas...
Nov 10 18:29:25 example.com quotaon.sh[452]: * Checking quotas...
Nov 10 18:29:26 example.com quotaon.sh[452]: ...done.
Nov 10 18:29:26 example.com quotaon.sh[452]: * Turning on quotas...
Nov 10 18:29:26 example.com quotaon.sh[452]: quotaon: using //aquota.group em /dev/sda1 [/]: Device or resource busy
Nov 10 18:29:26 example.com systemd[1]: quota.service: Main process exited, code=exited, status=1/FAILURE
Nov 10 18:29:26 example.com systemd[1]: Failed to start Check And Enable File System Quotas.
Nov 10 18:29:26 example.com systemd[1]: quota.service: Unit entered failed state.
Nov 10 18:29:26 example.com systemd[1]: quota.service: Failed with result 'exit-code'.


---

### Post by rhandy2 on 2015-11-12
service quota start fix it.

And Mask, service quotaon instaled by systemd.

---


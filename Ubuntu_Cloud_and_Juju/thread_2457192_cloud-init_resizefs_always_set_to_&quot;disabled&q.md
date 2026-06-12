---
title: "cloud-init resizefs always set to &quot;disabled&quot;"
date: 2021-01-27
forum: Ubuntu Cloud and Juju
---

### Post by mrbillwashere on 2021-01-27
(hope this is the right sub-forum for this question)

I've been trying to figure out this message using Ubuntu 18.4 (.5) LTS in /var/log/cloud-init.log for a while:

2021-01-26 22:42:45,291 - cc_resizefs.py[DEBUG]: Skipping module named resizefs, resizing disabled

I've tried various settings in my /etc/cloud/cloud.cfg.d/50_resizefs.cfg but doesn't seem to matter what I set.

```


growpart:
 mode: auto
 devices: ["/"]


resizefs:
 resize_rootfs: True

```
I've also tried with and without the resizefs section, and just a "resize_rootfs: true" under "growpart:" instead.

Because this is always disabled the provisioned machines will not allow cloud-init to adjust the root filesystem size.

Any suggestions?

---


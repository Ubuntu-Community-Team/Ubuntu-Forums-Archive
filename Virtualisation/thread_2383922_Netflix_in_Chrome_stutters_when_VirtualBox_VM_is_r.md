---
title: "Netflix in Chrome stutters when VirtualBox VM is running"
date: 2018-01-31
forum: Virtualisation
---

### Post by accounts0 on 2018-01-31
Running Ubuntu 16.04.3, VirtualBox 5.2.6 r120293, & Chrome 64.0.3282.119. Spectrum cable internet 100/10 on wired connection to router, only other device using internet is an Android smartphone idling.

Windows 7 Ultimate guest running SyncBackPro. Backup job is uploading to AWS S3, using 3 threads, bandwidth not rate limited & shows as going between 1.3 - 1.4 Mbps. Even with this task paused, I still get video stuttering on the host, so I don't think bandwidth is the problem.

The host box has an Intel i3 with 4 cores hyperthreaded, & 16GB RAM. The VM has 2x vCPUs, & 4GB RAM.

htop on host shows what appears to be an average of 30% - 50% CPU usage bars. States load average is at most 2.7.

I tried the following script to increase Chrome's priority, but it didn't work- htop showed all these chrome processes at 0 still.
```
#!/bin/bash
echo password | sudo -S nice -n -10 su -c /usr/bin/google-chrome-stable username
```

---

### Post by accounts0 on 2018-02-01
The issue went away when I turned off Hardware Acceleration in Chrome settings.

---


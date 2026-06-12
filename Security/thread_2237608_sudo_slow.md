---
title: "sudo slow"
date: 2014-08-02
forum: Security
---

### Post by cipherboy_loc on 2014-08-02
Okay, so this has continued happening after a complete reinstall of Ubuntu so not entirely sure what the problem is. The only thing I have not done yet is completely nuke my computer and start over with fresh Windows 8 and Ubuntu in UEFI+secureboot configuration (currently just regular EFI...). Also, if this isn't the right place, please move it. 

However the main problem is that the sudo command takes forever to complete. New computer, AMD A10 quad core 3.4GHz, 8GB RAM, HDD read/write speeds over 100MB/s+, so clearly not a undered power hardware issue. My test sample is:
```

time sudo date

```
Average real time for completely is right around 4.6 seconds currently, it peaked at 15.3 seconds and the min is right around 1-2 seconds. On another computer that is older but also running 14.04, the test case completes in under 0.005 seconds without fail. Note: this assumes sudo has been run previously and the password entered.

Running strace[[here]]("http://paste.ubuntu.com/7938696/") shows that the sendto calls are what is causing the delay in sudo. Strace with relevant systemcalls is [[here]]("http://paste.ubuntu.com/7938708/"). During the time sudo is running, CPU is not spiking...its more of a iowait type thing (in this case, on a sendto). This does not seem related to the posts I have seen with incorrect hostnames as my hostname has not been changed since I reinstalled the system. I have also tested this on every kernel since 3.8 on to my current kernel of 3.15 from the Ubuntu Kernel PPA (due to an unrelate(?) issue with network stats not being reported since 3.8 which was patched in 3.14 I believe) and have had the same issues. 

Other relevant or non-relevant information [[here]]("http://paste.ubuntu.com/7938769/"), including lsb_release, uname, hosts, hostname, uptime, nsswitch.conf, and resolv.conf. The only other thing to mention is I think that solving this will solve the issues I am having with Firefox taking a long time to resolve domain names (chromium and command line utilities don't have a similar issue)--both started at the same time and both disapear at the same time on the few occaions that it works correctly. 


Thanks,
Cipherboy

---


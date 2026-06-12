---
title: "Kernel Update Contains Fixes for 3 CVEs yet not a &quot;security&quot; update."
date: 2011-01-26
forum: Security
---

### Post by nutznboltz on 2011-01-26
There are 3 CVEs in the upstream kernel changes but due to upload issues the kernel update doesn't show up as a "security" one.

see:
aptitude changelog linux-image-2.6.32-28-generic

Version 2.6.32-27.49 is installed; version 2.6.32-27.50 has the CVE reports but version 2.6.32-28.55 is an artifact of incrementing the version number to overcome internal upload failures.

The USN mailing list does not even report that this update is a security one.

[https://lists.ubuntu.com/archives/ubuntu-security-announce/2011-January/date.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2011-January/date.html)

What gives?

---

### Post by nutznboltz on 2011-01-26
linux (2.6.32-28.50) lucid-proposed; urgency=low

  [ Tim Gardner ]

  * SAUCE: Change nodelayacct boot parameter polarity.
    - LP: #493156
  * [Config] CONFIG_TASK_DELAY_ACCT=y
    - LP: #493156

  [ Upstream Kernel Changes ]

  * ipc: initialize structure memory to zero for compat functions
  * tcp: Increase TCP_MAXSEG socket option minimum.
    - CVE-2010-4165
  * perf_events: Fix perf_counter_mmap() hook in mprotect()
    - CVE-2010-4169
  * af_unix: limit unix_tot_inflight
    - CVE-2010-4249

---


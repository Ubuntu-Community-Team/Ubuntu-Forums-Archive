---
title: "livepatch"
date: 2018-08-16
forum: Server Platforms
---

### Post by ivandeg18 on 2018-08-16
Hello. I use canonical-livepatch on Ubuntu Server 16.04 and 18.04

On 18.04 work great
> client-version: 8.0.2
architecture: x86_64
cpu-model: Intel(R) Xeon(R) CPU E3-1245 V2 @ 3.40GHz
last-check: 2018-08-16T16:11:49.566483343+05:00
boot-time: 2018-06-21T04:08:41+05:00
uptime: 1356h11m6s
status:
- kernel: 4.15.0-23.25-generic
  running: true
  livepatch:
    checkState: checked
    patchState: applied
    version: "42.1"
    fixes: |-
      * CVE-2018-10323
      * CVE-2018-10840
      * CVE-2018-10881
      * CVE-2018-1092
      * CVE-2018-1094
      * CVE-2018-11412
      * CVE-2018-11506
      * CVE-2018-12233
      * CVE-2018-13094
      * CVE-2018-13405
      * CVE-2018-13406
      * CVE-2018-5390
      * CVE-2018-5391
      * CVE-2018-7755
      * CVE-2018-8087

But on 16.04

> 
client-version: 8.0.2
architecture: x86_64
cpu-model: Intel(R) Xeon(R) CPU E5-2687W v4 @ 3.00GHz
last-check: 2018-08-16T15:29:37.849432371+05:00
boot-time: 2018-08-16T15:28:49+05:00
uptime: 51m45s
status:
- kernel: 4.15.0-30.32~16.04.1-generic
  running: true
  livepatch:
    checkState: checked
    patchState: nothing-to-apply
    version: ""
    fixes: ""


and

> client-version: 8.0.2
architecture: x86_64
cpu-model: Intel(R) Xeon(R) CPU E5-2687W v4 @ 3.00GHz
last-check: 2018-08-16T15:31:24.882579494+05:00
boot-time: 2018-07-05T09:21:31+05:00
uptime: 1014h18m15s
status:
- kernel: 4.13.0-37.42~16.04.1-generic
  running: true
  livepatch:
    checkState: checked
    patchState: nothing-to-apply
    version: ""
    fixes: ""

Why  patchState: nothing-to-apply and non fixes on vulnerable kernel on Ubuntu 16.04?
Thanks.

---

### Post by ivandeg18 on 2018-08-17
canonical-livepatch dont't working on HWE kernel.

 I run canonical-livepatch on non HWE kernel  kernel: 4.4.0-131.157-generic and fixes applied.

> status:
- kernel: 4.4.0-131.157-generic
  running: true
  livepatch:
    checkState: checked
    patchState: kernel-upgrade-required
    version: "42.1"
    fixes: |-
      * CVE-2017-17862
      * CVE-2018-1000004
      * CVE-2018-10323
      * CVE-2018-10840
      * CVE-2018-10877
      * CVE-2018-10881
      * CVE-2018-1092
      * CVE-2018-1093
      * CVE-2018-1094
      * CVE-2018-11412
      * CVE-2018-11506
      * CVE-2018-12233
      * CVE-2018-13094
      * CVE-2018-13405
      * CVE-2018-13406
      * CVE-2018-3665
      * CVE-2018-5390
      * CVE-2018-5391
      * CVE-2018-7755
      * CVE-2018-8087

---


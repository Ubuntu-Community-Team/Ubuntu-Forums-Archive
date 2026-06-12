---
title: "livepatch on 14.04 / patchs not applied"
date: 2017-07-19
forum: Server Platforms
---

### Post by gborysiak on 2017-07-19
Hi

I installed one month ago livepatch on ubuntu 14.04. 

Livepatch is running but it does nothing

client-version: "7.21"
machine-id: XXX
machine-token: YYYY
architecture: x86_64
cpu-model: Intel Core Processor (Haswell, no TSX)
last-check: 2017-07-19T08:25:52.550070916+02:00
boot-time: 2017-07-16T14:25:23+02:00
uptime: 66h55m10s
status:
- kernel: 4.4.0-83.106~14.04.1-generic
  running: true
  livepatch:
    checkState: checked
    patchState: nothing-to-apply
    version: ""
    fixes: ""

It should be on version 25.1 following LSN-0025-1 bulletin.

How to check if livepatch works ?

Regards,

Gregory Borysiak

---

### Post by Irihapeti on 2017-07-19
I ran into the same issue when I first installed livepatch. I've not discovered any way of checking that it's working, other than waiting for patches to be applied.

As I understand it, patches are only applied to a kernel that isn't the latest version. It looks like you may be running the 16.04 kernel, in which case you already have the latest kernel and thus there wouldn't be any patches to apply.

---

### Post by gborysiak on 2017-07-19
So I will wait for next major kernel bugs :-)

---

### Post by Irihapeti on 2017-07-19
I think that's the size of it. :) One day there will suddenly appear a list of patches.

---

### Post by deadflowr on 2017-07-19
There is no patch because you simple installed the newer kernel.
4.4.0-83.106 was an upgraded kernel version.
So it included any patch the livepatch would have installed.

Anyway, there is no livepatch for that version
(that version being 4.4.0-83.106 on 14.04
look at the list of affected kernels
```
| Kernel          | Version  | flavors                  |
|-----------------+----------+--------------------------|
| 4.4.0-21.37     | 25.1     | generic, lowlatency      |
| 4.4.0-22.39     | 25.1     | generic, lowlatency      |
| 4.4.0-22.40     | 25.1     | generic, lowlatency      |
| 4.4.0-24.43     | 25.1     | generic, lowlatency      |
| 4.4.0-28.47     | 25.1     | generic, lowlatency      |
| 4.4.0-31.50     | 25.1     | generic, lowlatency      |
| 4.4.0-34.53     | 25.1     | generic, lowlatency      |
| 4.4.0-36.55     | 25.1     | generic, lowlatency      |
| 4.4.0-38.57     | 25.1     | generic, lowlatency      |
| 4.4.0-42.62     | 25.1     | generic, lowlatency      |
| 4.4.0-43.63     | 25.1     | generic, lowlatency      |
| 4.4.0-45.66     | 25.1     | generic, lowlatency      |
| 4.4.0-47.68     | 25.1     | generic, lowlatency      |
| 4.4.0-51.72     | 25.1     | generic, lowlatency      |
| 4.4.0-53.74     | 25.1     | generic, lowlatency      |
| 4.4.0-57.78     | 25.1     | generic, lowlatency      |
| 4.4.0-59.80     | 25.1     | generic, lowlatency      |
| 4.4.0-62.83     | 25.1     | generic, lowlatency      |
| 4.4.0-63.84     | 25.1     | generic, lowlatency      |
| 4.4.0-64.85     | 25.1     | generic, lowlatency      |
| 4.4.0-66.87     | 25.1     | generic, lowlatency      |
| 4.4.0-67.88     | 25.1     | generic, lowlatency      |
| 4.4.0-70.91     | 25.1     | generic, lowlatency      |
| 4.4.0-71.92     | 25.1     | generic, lowlatency      |
| 4.4.0-72.93     | 25.1     | generic, lowlatency      |
| 4.4.0-75.96     | 25.1     | generic, lowlatency      |
| 4.4.0-77.98     | 25.1     | generic, lowlatency      |
| 4.4.0-78.99     | 25.1     | generic, lowlatency      |
| 4.4.0-79.100    | 25.1     | generic, lowlatency      |
| 4.4.0-81.104    | 25.1     | generic, lowlatency      |
| 4.4.0-83.106    | 25.1     | generic, lowlatency      |
| lts-4.4.0-21.37_14.04.1-lts-xenial | 14.04.1  | generic, lowlatency      |
| lts-4.4.0-22.39_14.04.1-lts-xenial | 14.04.1  | generic, lowlatency      |
| lts-4.4.0-22.40_14.04.1-lts-xenial | 14.04.1  | generic, lowlatency      |
| lts-4.4.0-24.43_14.04.1-lts-xenial | 14.04.1  | generic, lowlatency      |
| lts-4.4.0-28.47_14.04.1-lts-xenial | 14.04.1  | generic, lowlatency      |
| lts-4.4.0-31.50_14.04.1-lts-xenial | 14.04.1  | generic, lowlatency      |
| lts-4.4.0-34.53_14.04.1-lts-xenial | 14.04.1  | generic, lowlatency      |
| lts-4.4.0-36.55_14.04.1-lts-xenial | 14.04.1  | generic, lowlatency      |
| lts-4.4.0-38.57_14.04.1-lts-xenial | 14.04.1  | generic, lowlatency      |
| lts-4.4.0-42.62_14.04.1-lts-xenial | 14.04.1  | generic, lowlatency      |
| lts-4.4.0-45.66_14.04.1-lts-xenial | 14.04.1  | generic, lowlatency      |
| lts-4.4.0-47.68_14.04.1-lts-xenial | 14.04.1  | generic, lowlatency      |
| lts-4.4.0-51.72_14.04.1-lts-xenial | 14.04.1  | generic, lowlatency      |
| lts-4.4.0-53.74_14.04.1-lts-xenial | 14.04.1  | generic, lowlatency      |
| lts-4.4.0-57.78_14.04.1-lts-xenial | 14.04.1  | generic, lowlatency      |
| lts-4.4.0-59.80_14.04.1-lts-xenial | 14.04.1  | generic, lowlatency      |
| lts-4.4.0-62.83_14.04.1-lts-xenial | 14.04.1  | generic, lowlatency      |
| lts-4.4.0-63.84_14.04.2-lts-xenial | 14.04.2  | generic, lowlatency      |
| lts-4.4.0-64.85_14.04.1-lts-xenial | 14.04.1  | generic, lowlatency      |
| lts-4.4.0-66.87_14.04.1-lts-xenial | 14.04.1  | generic, lowlatency      |
| lts-4.4.0-70.91_14.04.1-lts-xenial | 14.04.1  | generic, lowlatency      |
| lts-4.4.0-71.92_14.04.1-lts-xenial | 14.04.1  | generic, lowlatency      |
| lts-4.4.0-72.93_14.04.1-lts-xenial | 14.04.1  | generic, lowlatency      |
| lts-4.4.0-75.96_14.04.1-lts-xenial | 14.04.1  | generic, lowlatency      |
| lts-4.4.0-78.99_14.04.2-lts-xenial | 14.04.2  | generic, lowlatency      |
| lts-4.4.0-79.100_14.04.1-lts-xenial | 14.04.1  | generic, lowlatency      |
| lts-4.4.0-81.104_14.04.1-lts-xenial | 14.04.1  | generic, lowlatency      |
```

The top section are the kernels for 16.04
and the bottom are the lts hardware stack enablement kernels.
Note that your kernel is missing from the list.


> How to check if livepatch works ?
Don't reboot.
Since you may have installed the new kernel with any other packages, it wouldn't have taken affect unless you rebooted.
If you kept on the older kernel, you would have gotten the livepatch for the older kernel.

One food for thought to see if live patching works would be to reboot into the older kernel (let's say try booting into 4.4.0-81)
Then let the system run for a moment.
(You can also try invoking snap  to update quicker with
```
snap refresh
```
then check if the patch gets applied to that kernel or not.)

---


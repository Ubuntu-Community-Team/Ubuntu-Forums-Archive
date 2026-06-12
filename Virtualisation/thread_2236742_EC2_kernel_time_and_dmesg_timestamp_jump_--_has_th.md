---
title: "EC2 kernel time and dmesg timestamp jump -- has the TSC bug returned in 14.04?"
date: 2014-07-28
forum: Virtualisation
---

### Post by Joe_CoT on 2014-07-28
I ran into an issue where kernel logs in syslog-ng would post for wildly inappropriate times -- months in the future.

I tracked it down to the source. The issue is the dmesg time jumping. Example here:

```

[    0.000000] Xen version: 3.4.3.amazon (preserve-AD)
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: 
[    0.000000] pcpu-alloc:
[    0.000000] pcpu-alloc: [0] 0 
[7493812.749226] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 430298
[7493812.749229] Policy zone: DMA32
[7493812.749232] Kernel command line: root=LABEL=cloudimg-rootfs ro console=hvc0 
[7493812.750892] PID hash table entries: 4096 (order: 3, 32768 bytes)
[7493812.750945] Checking aperture...
[7493812.760330] No AGP bridge found

```

This looks to be an issue with the Linux kernel trusting the TSC clock. The problem is discussed here:
[https://forums.aws.amazon.com/thread.jspa?threadID=59753](https://forums.aws.amazon.com/thread.jspa?threadID=59753)

Supposedly it was already fixed in 12.04:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/727459](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/727459)

I'm going to guess that the fix is broken again in 14.04. Have other people encountered this?

---


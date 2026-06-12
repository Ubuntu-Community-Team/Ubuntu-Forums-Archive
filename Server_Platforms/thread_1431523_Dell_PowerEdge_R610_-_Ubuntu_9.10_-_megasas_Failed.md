---
title: "Dell PowerEdge R610 - Ubuntu 9.10 - megasas: Failed to copy out to user sense data"
date: 2010-03-16
forum: Server Platforms
---

### Post by SupuS on 2010-03-16
Hi all

After kernel upgrade to latest version I get a lot of failure messages in syslog and dmesg:

```

Mar 16 22:50:30 s6 kernel: [515925.148335] megasas: Failed to copy out to user sense data
Mar 16 23:07:57 s6 kernel: [516970.118242] megasas: Failed to copy out to user sense data
Mar 16 23:07:57 s6 kernel: [516970.118341] megasas: Failed to copy out to user sense data
Mar 16 23:07:57 s6 kernel: [516970.125678] megasas: Failed to copy out to user sense data
Mar 16 23:07:57 s6 kernel: [516970.126046] megasas: Failed to copy out to user sense data
Mar 16 23:07:57 s6 kernel: [516970.131139] megasas: Failed to copy out to user sense data
Mar 16 23:07:57 s6 kernel: [516970.131507] megasas: Failed to copy out to user sense data
```

Kernel version:

```
Linux 2.6.31-20-server #57-Ubuntu SMP Mon Feb 8 09:59:59 UTC 2010 GNU/Linux
```

Server:

```
Dell PowerEdge R610
```

I found kernel bug report [http://bugzilla.kernel.org/show_bug.cgi?id=15001]("http://bugzilla.kernel.org/show_bug.cgi?id=15001") which is probably about same problem.

What is better solution? I don't want to build kernel from sources and apply the patch on live server. Should I uninstall latest kernel version and use previous version? Has anybody same problem on this server? Thanks for any suggestion.

SupuS

---

### Post by tgalati4 on 2010-03-16
Try to boot into the previous kernel and check your logs for errors.  You want to make sure that your system is stable with the older kernel before deleting the new kernel.

---

### Post by SupuS on 2010-03-17
> **tgalati4 said:**
> Try to boot into the previous kernel and check your logs for errors.  You want to make sure that your system is stable with the older kernel before deleting the new kernel.

Hi tgalati4

Thank you for replay. I booted with older version of kernel:

```
Linux 2.6.31-19-server #56-Ubuntu SMP Thu Jan 28 03:40:48 UTC 2010 x86_64 GNU/Linux
```

and everything is ok. So definetely this error is due to new kernel version. I didn't find any bug report about this error. I think that this is the time to report it :)

SupuS

---


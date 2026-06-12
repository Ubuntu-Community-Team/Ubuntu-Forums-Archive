---
title: "Kernel 6.6 RC (Release Candidate) Series"
date: 2023-09-10
forum: Ubuntu Development Version
---

### Post by Doug S on 2023-09-10
The kernel version 6.6 release candidate series has started, with [6.6-rc1]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.6-rc1/").

There are 126 default kernel configuration changes.

```
doug@s19:~$ uname -a
Linux s19 6.6.0-rc1-stock2 #1165 SMP PREEMPT_DYNAMIC Sun Sep 10 19:44:41 PDT 2023 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by xyz-t on 2023-09-13
Rc1 does not restart or shutdown. How to access* daily kernel prior 20230903? The bug was there that day..

---

### Post by Doug S on 2023-09-13
> **xyz-t said:**
> Rc1 does not restart or shutdown. How to access* daily kernel prior 20230903? The bug was there that day..

It restarts fine for me. I used:

```
doug@s19:~/kernel/linux$ [COLOR="#FF0000"]sudo shutdown -r now[/COLOR]
[sudo] password for doug:
Connection to s19 closed by remote host.
Connection to s19 closed.
```

I assume the dailies prior to Sept 3rd have been deleted. I do not know how to access them.

---

### Post by Doug S on 2023-09-14
I am getting this during boot:

```
Sep 13 11:14:34 s19 kernel: [    3.827410] ================================================================================
Sep 13 11:14:34 s19 kernel: [    3.827676] [COLOR="#FF0000"]UBSAN: shift-out-of-bounds[/COLOR] in drivers/hwmon/nct6775-core.c:1757:39
Sep 13 11:14:34 s19 kernel: [    3.827940] shift exponent -1 is negative
Sep 13 11:14:34 s19 kernel: [    3.828196] CPU: 9 PID: 822 Comm: sensors [COLOR="#FF0000"]Not tainted 6.6.0-rc1-stock2 [/COLOR]#1165
Sep 13 11:14:34 s19 kernel: [    3.828197] Hardware name: ASUS System Product Name/PRIME Z490-A, BIOS 9902 09/15/2021
Sep 13 11:14:34 s19 kernel: [    3.828198] Call Trace:
Sep 13 11:14:34 s19 kernel: [    3.828199]  <TASK>
Sep 13 11:14:34 s19 kernel: [    3.828201]  dump_stack_lvl+0x48/0x70
Sep 13 11:14:34 s19 kernel: [    3.828205]  dump_stack+0x10/0x20
Sep 13 11:14:34 s19 kernel: [    3.828206]  ubsan_epilogue+0x9/0x40
Sep 13 11:14:34 s19 kernel: [    3.828208]  __ubsan_handle_shift_out_of_bounds+0x10f/0x170
```

I can not find it now, but yesterday I found a reference that indicated this would be fixed by -RC2. I'll wait for -RC2 and then into it look deeper if it is not fixed.

EDIT: That reference was unrelated. I have submitted [a regression email]("https://lore.kernel.org/linux-hwmon/002101d9e7e0$f67c4490$e374cdb0$@telus.net/T/#u") upstream.

---

### Post by xyz-t on 2023-09-17
The bug was introduced in the drm-tip kernel on Sept 12. The correction was applied in today"s daily kernel. So rc2 runs fine. 

We made a bug report upstream and it did not take long to get the correction There was no daily kernel on the 16th.

Take care,

---

### Post by Doug S on 2023-09-17
> **xyz-t said:**
> The bug was introduced in the drm-tip kernel on Sept 12. The correction was applied in today"s daily kernel. So rc2 runs fine. 

We made a bug report upstream and it did not take long to get the correction There was no daily kernel on the 16th.

Take care,Could you provide a link to your upstream bug report, just for my curiosity/interest?

The isolation of my issue was too late for a fix for -rc2, but there should be a fix by -rc3.

I am just compiling -rc2 now.

---

### Post by IanW on 2023-09-18
[RC2 is up]("https://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2023-09-18/")(But failed self-tests) - 32 years _to the day_ since 0.1 released!

---

### Post by Doug S on 2023-09-19
Anyone else seeing these type of entries on /var/log/kern.log since kernel 6.6-rc1?

```
doug@s19:~/kernel/linux$ grep WQ_UNBOUND /var/log/kern.log
Sep 17 04:31:38 s19 kernel: [58526.387878] workqueue: output_poll_execute [drm_kms_helper] hogged CPU for >10000us 8 times, consider switching to WQ_UNBOUND
Sep 17 10:37:31 s19 kernel: [80479.577907] workqueue: update_pages_handler hogged CPU for >10000us 4 times, consider switching to WQ_UNBOUND
Sep 17 10:37:31 s19 kernel: [80479.578110] workqueue: update_pages_handler hogged CPU for >10000us 8 times, consider switching to WQ_UNBOUND
Sep 17 16:49:07 s19 kernel: [ 9311.522169] workqueue: output_poll_execute [drm_kms_helper] hogged CPU for >10000us 4 times, consider switching to WQ_UNBOUND
Sep 18 14:53:00 s19 kernel: [27559.346688] workqueue: output_poll_execute [drm_kms_helper] hogged CPU for >10000us 4 times, consider switching to WQ_UNBOUND
Sep 19 06:46:21 s19 kernel: [84760.660847] workqueue: output_poll_execute [drm_kms_helper] hogged CPU for >10000us 8 times, consider switching to WQ_UNBOUND
```

I am not aware of any negative side effect.

---

### Post by #&amp;thj^% on 2023-09-19
There has been a few report it: [https://lkml.org/lkml/2023/8/30/613](https://lkml.org/lkml/2023/8/30/613)
[https://gitlab.freedesktop.org/drm/intel/-/issues/9245](https://gitlab.freedesktop.org/drm/intel/-/issues/9245)
[https://lore.kernel.org/stable/20230901140403.2821777-1-imre.deak@intel.com/T/](https://lore.kernel.org/stable/20230901140403.2821777-1-imre.deak@intel.com/T/)
Looks to be more on the Intel side though, not seeing anything on mine current 6.5.0-5-generic

---

### Post by Doug S on 2023-09-19
> **1fallen said:**
> There has been a few report it: [https://lkml.org/lkml/2023/8/30/613](https://lkml.org/lkml/2023/8/30/613)
[https://gitlab.freedesktop.org/drm/intel/-/issues/9245](https://gitlab.freedesktop.org/drm/intel/-/issues/9245)
[https://lore.kernel.org/stable/20230901140403.2821777-1-imre.deak@intel.com/T/](https://lore.kernel.org/stable/20230901140403.2821777-1-imre.deak@intel.com/T/)
Looks to be more on the Intel side though, not seeing anything on mine current 6.5.0-5-genericThanks for the links. I had found some, but thanks for providing them for all. No, you wouldn't see it on kernel 6.5, as there is no way it would have been backported yet and I only see it as of kernel 6.6-rc1. I suspect (but am not certain) your link posts that predate 6.6-rc1 are from the linux_next source tree.

---

### Post by Doug S on 2023-09-25
> **Doug S said:**
> I am getting this during boot:

```
Sep 13 11:14:34 s19 kernel: [    3.827410] ================================================================================
Sep 13 11:14:34 s19 kernel: [    3.827676] [COLOR="#FF0000"]UBSAN: shift-out-of-bounds[/COLOR] in drivers/hwmon/nct6775-core.c:1757:39
Sep 13 11:14:34 s19 kernel: [    3.827940] shift exponent -1 is negative
Sep 13 11:14:34 s19 kernel: [    3.828196] CPU: 9 PID: 822 Comm: sensors [COLOR="#FF0000"]Not tainted 6.6.0-rc1-stock2 [/COLOR]#1165
Sep 13 11:14:34 s19 kernel: [    3.828197] Hardware name: ASUS System Product Name/PRIME Z490-A, BIOS 9902 09/15/2021
Sep 13 11:14:34 s19 kernel: [    3.828198] Call Trace:
Sep 13 11:14:34 s19 kernel: [    3.828199]  <TASK>
Sep 13 11:14:34 s19 kernel: [    3.828201]  dump_stack_lvl+0x48/0x70
Sep 13 11:14:34 s19 kernel: [    3.828205]  dump_stack+0x10/0x20
Sep 13 11:14:34 s19 kernel: [    3.828206]  ubsan_epilogue+0x9/0x40
Sep 13 11:14:34 s19 kernel: [    3.828208]  __ubsan_handle_shift_out_of_bounds+0x10f/0x170
```

I can not find it now, but yesterday I found a reference that indicated this would be fixed by -RC2. I'll wait for -RC2 and then into it look deeper if it is not fixed.

EDIT: That reference was unrelated. I have submitted [a regression email]("https://lore.kernel.org/linux-hwmon/002101d9e7e0$f67c4490$e374cdb0$@telus.net/T/#u") upstream.

This issue is fixed as of [kernel 6.6-rc3]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.6-rc3/"). See commit 2dd1d862817b.

---

### Post by jagsdesai on 2023-10-15
While trying to access: `https://kernel.ubuntu.com/~kernel-ppa/mainline/`

I'm getting this error:

```
404 Not Found
The requested URL was not found on this server.
Apache/2.4.41 (Ubuntu) Server at kernel.ubuntu.com Port 80
```

Anyone else getting the same error? Many thanks.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292865&stc=1[/IMG]

---

### Post by jeremy31 on 2023-10-15
> **jagsdesai said:**
> While trying to access: `https://kernel.ubuntu.com/~kernel-ppa/mainline/`

I'm getting this error:

```
404 Not Found
The requested URL was not found on this server.
Apache/2.4.41 (Ubuntu) Server at kernel.ubuntu.com Port 80
```

Anyone else getting the same error? Many thanks.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292865&stc=1[/IMG]

I would think everyone is getting that error, may be a while before we hear a reason for it

---

### Post by Doug S on 2023-10-16
I never had a problem accessing the Ubuntu mainline PPA in the last 24 hours. I see that -rc6 is not there yet. I compiled it myself yesterday.

```
doug@s19:~$ uname -a
Linux s19 6.6.0-rc6-stock #1186 SMP PREEMPT_DYNAMIC Sun Oct 15 14:40:25 PDT 2023 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by jagsdesai on 2023-10-16
> **Doug S said:**
> I never had a problem accessing the Ubuntu mainline PPA in the last 24 hours. I see that -rc6 is not there yet. I compiled it myself yesterday.

After seeing your post I just tried, and yes now the site opens just fine for me too. Thanks.

---

### Post by jeremy31 on 2023-10-16
See this on IRC #ubuntu-kernel earlier

Juerg Haefliger 
We're in the process of migrating away from some old machine that hosted kernel.ubuntu.com/~kernel-ppa/mainline to some new thing, hence the URL change. But it should redirect there.

---

### Post by Doug S on 2023-10-30
Kernel 6.6 has been released. The Ubuntu mainline builds are still broken. Excerpt from [IRC logs]("https://irclogs.ubuntu.com/2023/10/28/%23ubuntu-kernel.html"):

```
Eickmeyer:	mainline builds are broken atm due to internal infrastructure moves. no eta for a fix yet.
```

Anyway, I compiled myself:

```
doug@s19:~$ uname -a
Linux s19 6.6.0-stock #1187 SMP PREEMPT_DYNAMIC Mon Oct 30 07:28:49 PDT 2023 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by jagsdesai on 2023-10-30
> **Doug S said:**
> Kernel 6.6 has been released. The Ubuntu mainline builds are still broken. Excerpt from [IRC logs]("https://irclogs.ubuntu.com/2023/10/28/%23ubuntu-kernel.html"):

```
Eickmeyer:    mainline builds are broken atm due to internal infrastructure moves. no eta for a fix yet.
```

Thanks for the info. It sounds like I'm stuck with kernel 6.6 RC5 for a long while.

---

### Post by corradoventu on 2023-11-07
No more kernels after v6.6-rc5 dated 2023-10-08? 
or missing update on page [https://kernel.ubuntu.com/mainline/](https://kernel.ubuntu.com/mainline/) ???

---

